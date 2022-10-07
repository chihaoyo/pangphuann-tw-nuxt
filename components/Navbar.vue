<template>
<div class="navbar actions">
  <nuxt-link to="/" class="button home"></nuxt-link>
  <nuxt-link to="/about" class="button about">關於</nuxt-link>
  <a href="https://lin.ee/guB3RrI" class="button line" target="_blank"></a>
  <a href="https://www.instagram.com/pangphuann" class="button ig" target="_blank"></a>
  <a href="https://www.facebook.com/pangphuann" class="button fb" target="_blank"></a>
</div>
</template>

<style lang="scss">
.navbar {
  display: flex;
  align-items: center;
  margin: 1rem;
  > .button {
    margin-right: 0.25rem;
    background-color: transparent;
    color: var(--org-yellow-3);
    border: none;
    &.home {
      flex-shrink: 0;
      width: 64px;
      height: 64px;
      background-image: url("/images/navbar-home.png");
      background-size: contain;
      border-radius: 32px;
      border: none;
    }
    &.line {
      width: 40px;
      height: 40px;
      background-color: transparent;
      background-image: url("/images/navbar-line.png");
      background-size: contain;
      border-radius: 20px;
      border: none;
    }
    &.ig {
      width: 40px;
      height: 40px;
      background-color: transparent;
      background-image: url("/images/navbar-ig.png");
      background-size: contain;
      border-radius: 20px;
      border: none;
    }
    &.fb {
      width: 40px;
      height: 40px;
      background-color: transparent;
      background-image: url("/images/navbar-fb.png");
      background-size: contain;
      border-radius: 20px;
      border: none;
    }
    > span {
    }
  }
}
</style>
