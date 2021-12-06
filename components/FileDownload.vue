<template>
  <div class="file-download">
    <UilFileDownload size="1.75rem" class="mr-1" />
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
  align-items: center;
  color: $blue;
  margin-bottom: 2rem;
}
</style>