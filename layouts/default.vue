<template>
  <Nuxt />
</template>

<script></script>

<style lang="scss">
@import url(https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;600;700&display=swap);
@import url(https://fonts.googleapis.com/css2?family=Play:wght@400;700&display=swap);
@import '~/assets/style/button.scss';
@import '~/assets/style/container.scss';
@import '~/assets/style/helpers.scss';
@import '~/assets/style/link.scss';
@import '~/assets/style/reset.scss';

[lazy] {
  opacity: 0 !important;
  transition: opacity 0.3s !important;
}

[lazy='loaded'] {
  opacity: 1 !important;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
