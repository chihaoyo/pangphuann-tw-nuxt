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
    <div class="item" v-for="entry of entries" :key="entry.k"><label class="key">{{ entry.k }}</label><label class="value">{{ entry.v }}</label></div>
  </div>
</footer>
</template>

<script>
const axios = require('axios')
const cheerio = require('cheerio')

export default {
  async fetch() {
    const publicURL = 'https://docs.google.com/document/d/e/2PACX-1vSXefK9vJKhIdaoOgkIFmpMa4O04ykSF3ThFUtTj-sNXLNmlgAMblm5gu3YcObVUzZwPjb0eIAo9jtq/pub'
    let gdoc = await axios.get(publicURL)
    gdoc = gdoc.data
    gdoc = gdoc.split('\n').map(line => line.trim())
    gdoc = gdoc.join('')
    gdoc = gdoc.replace(/<head[^>]*>.*<\/head>/, '')
    gdoc = gdoc.replace(/<style[^>]*>.*<\/style>/, '')
    gdoc = gdoc.replace(/<script[^>]*>.*<\/script>/, '')
    gdoc = gdoc.replace(/<div id="banners">.*<\/div><div id="contents">/, '<div id="contents">')
    gdoc = gdoc.replace(/<span[^>]*><\/span>/g, '')
    gdoc = gdoc.replace(/<p[^>]*>\s*<\/p>/g, '')
    gdoc = gdoc.replace(/<a[^>]*>\s*<\/a>/g, '')

    let $ = cheerio.load(gdoc)
    $('#header, #footer').remove()
    $('#contents').removeAttr('id').children().first().addClass('content')
    gdoc = $('div.content').html()
    $ = cheerio.load('<div class="content">' + gdoc + '</div>')

    const tables = $('table')
    for(let i = 0; i < tables.length; i++) {
      const table = tables.eq(i)
      const cells = table.find('td')
      const firstCell = cells.eq(0)
      const type = firstCell.text()
      if(type === 'end') {
        table.nextAll().remove()
        table.remove()
      }
    }

    const infoTable = $('table').eq(0)
    const cells = infoTable.find('td')
    for(let i = 0; i < cells.length; i += 2) {
      const k = cells.eq(i).text()
      const v = cells.eq(i + 1).text()
      this.entries.push({ k, v })
    }
  },
  data() {
    return {
      entries: []
    }
  }
}

</script>

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
