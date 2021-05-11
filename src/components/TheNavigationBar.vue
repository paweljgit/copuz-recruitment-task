<template>
<nav class="navigation-bar">
  <TheLogo />
  <TheSocialMediaButton />
</nav>
</template>

<script>
import TheLogo from './TheLogo'
import TheSocialMediaButton from './TheSocialMediaButton'

export default {
  name: 'TheNavigationBar',
  components: {
    TheLogo, TheSocialMediaButton
  }
}
</script>

<style scoped lang="scss">
.navigation-bar {
  display: flex;
  min-width: 100%;
  justify-content: space-between;
  margin-bottom: var(--base-padding);
}
</style>
