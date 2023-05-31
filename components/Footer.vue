<template>
<footer>
  <div class="map">
    <nuxt-link to="/" class="inverted">首頁</nuxt-link>
    <nuxt-link to="about" class="inverted">關於放伴</nuxt-link>
    <a href="https://lin.ee/guB3RrI" class="button line" target="_blank"></a>
    <a href="https://www.instagram.com/pangphuann" class="button ig" target="_blank"></a>
    <a href="https://www.facebook.com/pangphuann" class="button fb" target="_blank"></a>
  </div>
  <div class="info">
    <div class="item"><label class="key">立案證號</label><label class="value">台內團字第 1090044406 號</label></div>
    <div class="item"><label class="key">法人登記字號</label><label class="value">法人登記他字第 000210 號</label></div>
    <div class="item"><label class="key">公益勸募字號</label><label class="value">衛部救字第 1111362376 號</label></div>
  </div>
</footer>
</template>

<style lang="scss">
footer {
  margin: 4rem 0;
  > .map {
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 2rem;
    margin: 0 auto 1rem;
    padding: 2rem;
    background: var(--org-text);
    color: var(--org-paper);
    max-width: 16rem;
    > a {
      margin: 0.5rem 0;
    }
    > .button {
      margin: 0.5rem 0 0;
      &.line {
        width: 40px;
        height: 40px;
        background-color: transparent;
        background-image: url("/images/footer-line.png");
        background-size: contain;
        border-radius: 20px;
        border: none;
        opacity: 0.35;
      }
      &.ig {
        width: 40px;
        height: 40px;
        background-color: transparent;
        background-image: url("/images/footer-ig.png");
        background-size: contain;
        border-radius: 20px;
        border: none;
        opacity: 0.35;
      }
      &.fb {
        width: 40px;
        height: 40px;
        background-color: transparent;
        background-image: url("/images/footer-fb.png");
        background-size: contain;
        border-radius: 20px;
        border: none;
        opacity: 0.35;
      }
    }
  }
  > .info {
    border: 2px solid var(--org-text);
    border-radius: 2rem;
    margin: 0 auto;
    padding: 2rem;
    max-width: 16rem;
    .item {
      margin-bottom: 0.25rem;
    }
    .key, .value {
      display: block;
    }
    .key {
      font-size: 0.75rem;
    }
    .value {
      font-size: 0.875rem;
    }
  }
}
</style>
