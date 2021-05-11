<template>
<main class="calculator">
  <header class="header">
    <h1 class="header__title">Recruitment task</h1>
    <h2 class="header__subtitle">with a twist</h2>
  </header>
  <p class="header__info">My task was to write a calculator that would do "something" if the result of the calculation will be the number 9.</p>

  <form class="magic-calculator">
    <div>
      <input 
        id="first-number"
        type="number" 
        v-model.number="firstNumber" 
        class="magic-calculator__input"
      />
      <label 
        for="first-number"
        class="magic-calculator__label"
      >
        Enter number
      </label>
    </div>
    <div class="magic-calculator__toggler">
      <input 
        id="toggler"
        type="checkbox" 
        v-model="whichMath" 
        true-value="adding"
        false-value="multiply"
        class="pointer"
      />
      <label 
        for="toggler"
        class="magic-calculator__label"
      >
        x / +
      </label>
    </div>
    <div>
      <input 
        id="second-number"
        type="number" 
        v-model.number="secondNumber" 
        class="magic-calculator__input"
      />
      <label 
        for="second-number"
        class="magic-calculator__label"
      >
        Enter number
      </label>
    </div>
    <div class="magic-calculator__equal-sign">
      =
    </div>
    <div>
      <input 
        id="result"
        type="number" 
        v-model="calculator" 
        readonly="readonly"
        class="magic-calculator__input"
        :style="getStyleForMagicNumber"
      />
      <label 
        for="result"
        class="magic-calculator__label"
      >
        Result
      </label>
    </div>
  </form>
  <footer class="calculator__footer">
    <p>Thanks for the opportunity to complete the recruitment task. Have a nice day. <a href="https://github.com/paweljgit/" target="_blank" rel="noopener">PJ</a></p>
  </footer>
</main> 
</template>

<script>
export default {
  name: 'TheMagicCalculator',
  data() {
    return {
      firstNumber: null,
      secondNumber: null,
      whichMath: "multiply",
      specialNuber: 9,
      result: 0,
    }
  },
  computed: {
    calculator() {
      if (this.firstNumber && this.secondNumber) {
        if (this.whichMath === "multiply") {
          let calculationResult = this.firstNumber * this.secondNumber
          this.setResult(calculationResult)
          this.checkIsItSpecialNumber(calculationResult)
          return calculationResult
        } else {
          let calculationResult = this.firstNumber + this.secondNumber
          this.setResult(calculationResult)
          this.checkIsItSpecialNumber(calculationResult)
          return calculationResult
        }   
      } else {
        return ''
      }
    },
    getStyleForMagicNumber() {
      return this.result === this.specialNuber ? 'font-weight: bold' : ''  
    }
  },
  methods: {
    setResult(e) {
      this.result = e
    },
    checkIsItSpecialNumber(number) {
      if (number === this.specialNuber) {
        this.$emit('set-is-suprise-visible',true)
      } else {
        this.$emit('set-is-suprise-visible',false)
      }
    }
  }
}
</script>

<style scoped lang="scss">
.calculator {
  display: block;
  width: 100%;
  position: relative;

  @media (min-width: 650px) {
    width: 50%;
    height: 380px;
    
    .calculator__footer {
      position: absolute;
      bottom: 0px;
    }
  }
}

.header {
border-left: 5px solid white;
padding-left: 15px;
margin-bottom: var(--base-elements-margin);

  &__title, &__subtitle {

    text-transform: uppercase;
    margin: 0px;
    padding: 0px;
  }
  &__title {
    font-size: 36px;
  }
  &__subtitle {
    font-size: 26px;
    color: white;
  }
  &__info {
    margin-bottom: var(--base-elements-margin);
    line-height: 125%;
  }
}

.magic-calculator {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 10px;
  margin-bottom: var(--base-elements-margin);
  
  @media (min-width: 480px) {
    flex-direction: row;
  }

  * {
    width: 100%;
  }

  &__input {
    display: block;
    background-color: rgba(255, 255, 255, 0.555);
    border: none;
    border-bottom: 2px solid rgb(0, 0, 0);
    padding: 5px;
    min-width: 70px;
    height: 26px;
    margin: 0px;
    text-align: center;
    border-top-left-radius: 5px;
    border-top-right-radius: 5px;
    
    &::-webkit-inner-spin-button, 
    &::-webkit-outer-spin-button { 
      -webkit-appearance: none; 
      margin: 0; 
    }
  }

  &__label {
    display: block;
    width: 100%;
    font-size: 9px;
    text-align: center;
    background-color: yellow;
    margin: 0px;
    padding: 2px 0px;
    border-bottom-left-radius: 5px;
    border-bottom-right-radius: 5px;
  }

  &__toggler {
    position: relative;
    min-width: 40px;
    max-width: 40px;

    input {
      appearance: none;
      width: 40px;
      height: 26px;
      display: block;
      position: relative;
      border-top-left-radius: 5px;
      border-top-right-radius: 5px;
      overflow: hidden;
      outline: none;
      border: none;
      cursor: pointer;
      background-color: rgba(255, 255, 255, 0.555);
      transition: background-color ease 0.3s;
      border-bottom: 2px solid black;
      margin: 0px;
    }

    input:before {
      content: "";
      display: block;
      position: absolute;
      z-index: 2;
      width: 16px;
      height: 16px;
      background: #fff;
      left: 4px;
      top: 4px;
      border-radius: 50%;
      transition: all cubic-bezier(0.3, 1.5, 0.7, 1) 0.3s;
    }

    input:checked:before {
      left: 20px;
    }
  }

  &__equal-sign {
    text-align: center;
    font-weight: bold;
    font-size: x-large;
  }

}

</style>
