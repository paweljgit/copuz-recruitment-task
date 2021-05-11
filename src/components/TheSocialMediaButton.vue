<template>
<a 
  href="https://www.instagram.com/copuzcom/" 
  target="_blank" 
  class="social-media-button" 
  aria-label="Instagram link"
  rel="noopener"
/>
</template>

<script>
export default {
  name: 'TheSocialMediaButton'
}
</script>

<style scoped lang="scss">
.social-media-button {
  display: block;
  width: var(--navigation-elements-height);
  height: var(--navigation-elements-height);
  background: 
    url('~@/assets/awesome-insta-icon.svg') 
    left center
    /contain 
    no-repeat;
  border: 0px;
  opacity: 0.3;
}
</style>
