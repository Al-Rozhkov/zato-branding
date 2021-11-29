<template>
  <div
    v-if="link"
    class="pt-4 pb-4 lg:px-8 flex flex-col sm:flex-row justify-between"
  >
    <a
      :href="link"
      target="_blank"
      rel="noopener"
      class="
        text-gray-600
        dark:text-gray-400
        text-sm
        font-medium
        hover:underline
        flex
        items-center
      "
    >
      github
    </a>
    <span
      class="
        text-gray-600
        dark:text-gray-400
        text-sm
        font-medium
        flex
        items-center
      "
    >
      updated at
    </span>
  </div>
</template>

<script>
export default {
  props: {
    document: {
      type: Object,
      required: true,
    },
  },
  // computed: {}
}
</script>
