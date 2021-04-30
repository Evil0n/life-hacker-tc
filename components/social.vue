<template>
  <div class="social">
    <div class="social__icons">
      <div class="social__social social__social--tw">
        <svg>
          <use xlink:href="~/assets/icons.sprite.svg#tw-usage"></use>
        </svg>
      </div>
      <div class="social__social social__social--vk">
        <svg>
          <use xlink:href="~/assets/icons.sprite.svg#vk-usage"></use>
        </svg>
      </div>
      <div class="social__social social__social--fb">
        <svg>
          <use xlink:href="~/assets/icons.sprite.svg#fb-usage"></use>
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Social',
}
</script>

<style scoped lang="scss">
.social {
  &__icons,
  &__social {
    display: flex;
    align-items: center;
  }

  &__social {
    width: 2.5rem;
    height: 2.5rem;
    overflow: hidden;
    cursor: pointer;
    justify-content: center;
    border-radius: 50%;
    background-color: #7dbfff;
    transition: background-color 0.3s ease;

    &:not(:last-of-type) {
      margin-right: 0.625rem;
    }

    svg {
      width: 1.3125rem;
      height: 1.125rem;
      display: block;
      transition: fill 0.3s ease;
      fill: #014170;
    }

    &__social:hover {
      background-color: #fff;
    }
  }

  &--white &__social {
    svg {
      fill: #fff;
    }

    &:hover svg {
      fill: #ed5e42;
    }
  }
}
</style>
