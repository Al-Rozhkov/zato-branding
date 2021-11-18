<template>
  <aside class="sidebar" :class="{ hidden: !menu }">
    <div class="sidebar__sticky">
      <AppLogo class="logo" />

      <ul class="menu">
        <li
          v-for="(docs, category) in categories"
          :key="category"
          :class="{ active: isCategoryActive(docs) }"
        >
          <p v-if="category" class="menu-group">
            {{ category }}
          </p>
          <ul class="menu">
            <li v-for="doc of docs" :key="doc.slug" class="menu-item">
              <NuxtLink
                :to="doc.path"
                class="menu-link"
                exact-active-class="exact-active"
              >
                {{ doc.menuTitle || doc.title }}
              </NuxtLink>
            </li>
          </ul>
        </li>
      </ul>

    </div>
  </aside>
</template>

<script>
import groupBy from 'lodash.groupby'

export default {
  data: () => ({
    docs: [],
  }),

  async fetch() {
    this.docs = await this.$content('/', { deep: true })
      .only(['title', 'menuTitle', 'category', 'slug', 'version', 'to'])
      .sortBy('position', 'asc')
      .fetch()
  },

  computed: {
    categories() {
      return groupBy(this.docs, 'category')
    },
    menu: {
      get() {
        return this.$store.state.menu.open
      },
      set(val) {
        this.$store.commit('menu/toggle', val)
      },
    },
  },

  methods: {
    isCategoryActive(documents) {
      return documents.some((document) => document.to === this.$route.fullPath)
    },
  },
}
</script>

<style lang="scss" scoped>
.logo {
  display: block;
  height: 3.5rem;
  margin-bottom: 1rem;

  svg {
    width: 100%;
    height: 100%;
  }
}

@include media-breakpoint-up(md) {
  .sidebar__sticky {
    padding-left: 3.5rem;
  }
  .logo {
    margin-bottom: 2rem;
    margin-left: -2.5rem;
  }
}
</style>