<template>
<div class="page about">
  <div v-for="section of sections" :key="section.title" class="section" :class="section.classes" :style="section.styles">
    <div class="image" :style="section.backgroundImageStyles"></div>
    <h2><span>{{ section.title }}</span></h2>
    <div class="content" v-html="section.html"></div>
  </div>
</div>
</template>

<script>
import { getDoc, structureDoc } from '~/lib/gdoc'
import { generateMeta } from '~/lib/meta'

const defaultLocale = '_tw'

export default {
  async asyncData({ app, query }) {
    const url = 'https://docs.google.com/document/d/e/2PACX-1vS59tq3y6iyfbJ2GdjR2cg7mCV0Hk9rks19Ya95Z3SWMyL3dzcm6yzEhRhGOflabwJPhtisy0wP5iJT/pub'
    const doc = await getDoc(url, defaultLocale, true)
    const structuredDoc = structureDoc(doc.html, ['h2'])
    const sections = []
    for(let i = 0; i < doc.sections.length; i++) {
      const section = Object.assign({}, doc.sections[i], structuredDoc[i])
      section.classes = [
        ...(section.name ? [section.name] : []),
        ...(section.classes ? [section.classes] : []),
        ...(section.image ? ['has-image'] : [])
      ].join(' ')
      section.backgroundImageStyles = Object.assign({},
        section.image ? { backgroundImage: `url("${section.image}")` } : {}
      )
      sections.push(section)
    }
    return {
      doc,
      sections
    }
  },
  head() {
    return generateMeta(this.doc.title)
  }
}
</script>

<style lang="scss">
</style>
