<template>
  <aside v-if="toc.length" class="sidebar">
    <nav class="sidebar__sticky">
      <scrollactive
        highlight-first-item
        active-class="nuxt-link-active"
        :offset="0"
        tag="ul"
        class="menu"
      >
        <li
          v-for="link of toc"
          :key="link.id"
          class="menu-item"
          :class="`depth--${link.depth}`"
        >
          <a :href="`#${link.id}`" class="menu-link scrollactive-item">{{ link.text }}</a>
        </li>
      </scrollactive>
    </nav>
  </aside>
</template>

<script>
export default {
  props: {
    toc: {
      type: Array,
      default: () => [],
    },
  },
}
</script>

<style lang="scss" scoped>
.sidebar {
  font-size: 0.85rem;
}
</style>