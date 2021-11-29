<template>
  <nuxt-link class="logo" to="/">
    <img src="/logo.png" alt="Ассоциация ЗАТО атомной промышленности" />
  </nuxt-link>
</template>

<style lang="scss" scoped>
.logo {
  display: block;
  max-width: 12rem;
  margin-bottom: 1rem;

  img {
    max-width: 100%;
    height: auto;
  }

  svg {
    width: 100%;
    height: 100%;
  }
}

@include media-breakpoint-up(md) {
  .logo {
    margin-bottom: 2rem;
    margin-left: -2.5rem;
  }
}
</style>