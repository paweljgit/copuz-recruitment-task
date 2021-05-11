<template>
<div class="wrapper">
  <transition name="fade">
    <div v-if="isSupriseVisible" class="suprise" >
      <TheSupriseMessage />
      <img 
        src="~@/assets/suprise-dog.png"
        class="suprise__dog-photo"
        alt="Suprise dog"
      />
    </div>
  </transition>
</div>
</template>

<script>
import TheSupriseMessage from './TheSupriseMessage'
export default {
  name: 'TheSuprise',
  components: {TheSupriseMessage},
  props: {
    isSupriseVisible: {
      data: Boolean,
      required: true
    }
  }
}
</script>

<style scoped lang="scss">

.wrapper {
  display: block;
  width: 100%;

  @media (min-width: 650px) {
    width: 50%;
    height: 380px;
  }
}

.suprise {
  width: 100%;
  position: relative;
  margin-bottom: var(--base-elements-margin);
  
  @media (min-width: 480px) {
    padding-left: 50px;
  }

  &__dog-photo {
    width: 100%;
  }
}

// Fade animation

.fade-enter-active {
  animation: fade-in 0.5s ease-in;
  opacity: 0;
}

.fade-leave-active {
  animation: fade-out 0.5s ease-out;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}

@keyframes fade-out {
  from { opacity: 1 }
  to { opacity: 0 }
}

@keyframes fade-in {
  from { opacity: 0 }
  to { opacity: 1 }
}

</style>