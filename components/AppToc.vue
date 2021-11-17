<template>
  <aside v-if="toc.length" class="sidebar">
    <nav class="sidebar__sticky">
      <scrollactive
        highlight-first-item
        active-class="active"
        :offset="0"
        tag="ul"
        class="menu"
      >
        <li
          v-for="link of toc"
          :key="link.id"
          class="menu-item"
          :class="{
            'border-t border-dashed dark:border-gray-800 first:border-t-0':
              link.depth === 2,
          }"
        >
          <a
            :href="`#${link.id}`"
            class="menu-link"
            :class="{
              'py-2': link.depth === 2,
              'ml-2 pb-2': link.depth === 3,
              'ml-3 pb-2': link.depth === 4,
              'ml-4 pb-2': link.depth === 5,
              'ml-5 pb-2': link.depth === 6,
            }"
            >{{ link.text }}</a
          >
        </li>
      </scrollactive>
    </nav>
  </aside>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  props: {
    toc: {
      type: Array,
      default: () => [],
    },
  },
  computed: {
    ...mapGetters(['settings']),
  },
}
</script>

<style lang="scss" scoped>
.sidebar {
  font-size: 0.85rem;
}
</style>