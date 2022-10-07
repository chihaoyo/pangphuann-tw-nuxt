<template>
<main>
  <navbar />
  <nuxt />
  <Foooter />
</main>
</template>

<script>
import Navbar from '~/components/Navbar'
import Foooter from '~/components/Footer'

export default {
  components: {
    Navbar,
    Foooter
  }
}
</script>

<style lang="scss">
@import '~assets/styles/resources';
@import '~assets/styles/common';

:root {
  --org-text: #36321C; // #404040;
  --org-paper: #FFFDF5;
  --org-yellow-1: #FFF5CC;
  --org-yellow-2: #FFE680;
  --org-yellow-3: #FFD11A;
  --org-background: var(--org-yellow-1);
}
main {
  max-width: 60rem;
  margin: 0 auto;
}
</style>
