<template>
  <div class="page">
    <AppToc v-if="!document.fullscreen" :toc="document.toc" class="toc" />

    <div class="page__content">
      <article>
        <h1 class="page-title">
          {{ document.title }}
        </h1>
        <div v-if="document.subtitle" class="subtitle">
          <p>
            {{ document.subtitle }}
          </p>
        </div>

        <NuxtContent :document="document" />
      </article>

      <!-- <AppPrevNext :prev="prev" :next="next" /> -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'PageSlug',

  async asyncData({ $content, app, params, error }) {
    const path = `/${params.pathMatch || 'index'}`
    const [document] = await $content({ deep: true }).where({ path }).fetch()
    if (!document) {
      return error({ statusCode: 404, message: 'Page not found' })
    }

    const [prev, next] = await $content('/', { deep: true })
      .only(['title', 'path', 'to'])
      .sortBy('position', 'asc')
      .surround(document.path, { before: 1, after: 1 })
      .fetch()

    return {
      document,
      prev,
      next,
    }
  },

  head() {
    return {
      title: this.document.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.document.description,
        },
        // Open Graph
        { hid: 'og:title', property: 'og:title', content: this.document.title },
        {
          hid: 'og:description',
          property: 'og:description',
          content: this.document.description,
        },
        // Twitter Card
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: this.document.title,
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content: this.document.description,
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
@include media-breakpoint-up(lg) {
  .page {
    display: grid;
    gap: $spacer;
    grid-template-columns: 1fr 4fr;
  }

  .page__content {
    grid-column: 2 / 3;
  }
}
</style>