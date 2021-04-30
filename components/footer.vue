<template>
  <footer class="footer">
    <div class="container footer__container">
      <slot />
      <div class="footer__copyright">
        <a href="https://lifehacker.ru" class="link">Лайфхакер</a>
        <span class="footer__copyright-separator"></span>
        <a href="https://cordiant.ru" class="link">Cordiant</a>
        <span>© 2021</span>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'PageFooter',
}
</script>

<style scoped lang="scss">
.footer {
  padding: 2.5rem 0 1rem;
  margin-top: auto;

  &__container {
    text-align: center;

    @media (min-width: 768px) {
      display: flex;
      justify-content: space-between;
      align-content: flex-end;
      height: 100%;
      text-align: left;
    }
  }

  &__copyright {
    font-size: 12px;
    line-height: 15px;
    display: inline-flex;
    align-items: center;
    color: #fff;

    span {
      line-height: 1.25rem;
    }

    a {
      margin-right: 5px;

      &:not(:first-of-type) {
        @media (min-width: 768px) {
          margin-left: 5px;
        }
      }

      @media (min-width: 1280px) {
        transition: color 0.3s ease;
      }
    }

    @media (min-width: 768px) {
      order: 1;
    }
  }

  &__copyright-separator {
    border-left: 1px solid #fff;
    margin-right: 5px;
    height: 12px;
    display: inline-block;
  }

  @media (min-width: 1280px) {
    position: fixed;
    left: 0;
    bottom: 0;
    width: 100%;
    z-index: 999;
    padding-top: 0;
  }
}
</style>
