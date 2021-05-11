<template>
<div class="wrapper">
  <div class="suprise-pic" />
  <div class="glass-card">
    <slot></slot>
  </div>
</div>



</template>

<script>
export default {
  name: 'GlassCard',
}
</script>

<style scoped lang="scss">

.wrapper {
  width: calc(100vw - 40px);
  max-width: 768px;
  position: relative;  
}

.glass-card {
  position: relative;
  width: 100%;
  min-height: 400px;
  padding: var(--base-padding);
  background: rgba( 255, 255, 255, 0.25 );
  backdrop-filter: blur( 12.5px );
  -webkit-backdrop-filter: blur( 12.5px );
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.068);
  box-shadow: rgba(0, 0, 0, 0.56) 0px 22px 70px 4px;
  display: flex;
  flex-wrap: wrap;
  
  @media (min-width: 650px) {
    flex-direction: row-reverse;
  }
}

.suprise-pic {
  position: absolute;
  top: -5%;
  left: -5%;
  width: 110%;
  height: 110%;
  background: 
    url('~@/assets/suprise-dog.png') 
    left center
    /contain 
    no-repeat;
  opacity: 0.3;
}
</style>
