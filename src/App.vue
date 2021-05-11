<template>
  <TheGlassCard>
    <TheNavigationBar />
    <TheSuprise 
      :isSupriseVisible="isSupriseVisible"
    />
    <TheMagicCalculator 
      @set-is-suprise-visible="setIsSupriseVisible"
    />
  </TheGlassCard>
</template>

<script>
import TheGlassCard from './components/TheGlassCard'
import TheNavigationBar from './components/TheNavigationBar'
import TheMagicCalculator from './components/TheMagicCalculator'
import TheSuprise from './components/TheSuprise'


export default {
  name: 'App',
  components: {
    TheGlassCard, TheNavigationBar, TheMagicCalculator, TheSuprise
  },
  data() {
    return {
      isSupriseVisible: false
    }
  },
  methods: {
    setIsSupriseVisible(e) {
      e ? this.isSupriseVisible = true : this.isSupriseVisible = false  
    }
  }
}
</script>
