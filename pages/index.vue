<template>
<div class="page index"></div>
</template>

<script>
export default {
  asyncData({ app, query }) {
    const url = 'https://docs.google.com/document/d/e/2PACX-1vTDqM9y8HpAPL9J7RaYfcXF9eBJoVngDK5FGhP0GnkKCygEd63QHsNpslp1pA9ucon4xnaxwwIynQ95/pub'
    return {
      url
    }
  }
}
</script>

<style lang="scss">
</style>
