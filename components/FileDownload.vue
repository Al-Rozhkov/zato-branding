<template>
  <div class="file-download">
    <UilFileDownload />
    <div><slot /></div>
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

<style lang="scss" scoped>
.file-download {
  display: flex;
}
</style>