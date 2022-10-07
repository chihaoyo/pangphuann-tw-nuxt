<template>
<div class="page events">
  <p class="notice"><span class="emoji">⚠️</span><span class="message">活動列表即將上線</span><span class="emoji">⚠️</span></p>
</div>
</template>

<script>
// import { getDoc, structureDoc } from '~/lib/gdoc'
import { generateMeta } from '~/lib/meta'

export default {
  head() {
    return generateMeta('活動列表')
  }
}
</script>

<style lang="scss">
.page.events {
  .notice {
    display: flex;
    align-items: center;
    justify-content: center;
    > .emoji {
      margin: 0 0.25rem;
      font-size: 1.25rem;
    }
    > .message {
      font-size: 0.875rem;
    }
  }
}
</style>
