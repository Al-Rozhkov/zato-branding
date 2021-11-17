<template>
  <div>
    <UilFileDownload />
    <slot />
  </div>
</template>

<script>
import { UilFileDownload } from '@iconscout/vue-unicons'

export default {
  components: {
    UilFileDownload,
  },
}
</script>