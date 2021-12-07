<template>
  <div class="intro">
    <h1 class="intro-headline">
      Руководство по&nbsp;использованию фирменного стиля Ассоциации ЗАТО атомной
      промышленности
    </h1>
    <div class="intro-ill">
      <nuxt-img src="/intro.jpg" class="img-fluid"></nuxt-img>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.intro {
  display: flex;
  align-items: center;
  padding: 1rem;
}

.intro-headline {
  padding: 1rem;
}

.intro-ill {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;

  img {
    max-height: 90vh;
  }
}

@include media-breakpoint-up(md) {
  .intro-headline {
    flex: 1 0 35%;
    max-width: 35%;
    order: 2;
  }

  .intro-ill {
    flex: 1 0 65%;
    max-width: 65%;
    order: 1;
  }
}
</style>
