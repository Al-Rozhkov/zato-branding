<template>
  <div class="cnt">
    <div>
      <AppNav />
    </div>

    <Nuxt />
  </div>
</template>

<style lang="scss" scoped>
@include media-breakpoint-up(md) {
  .cnt {
    display: grid;
    grid-template-columns: 1fr 5fr;
  }
}
</style>