<template>
  <div class="calculator h-[320px] w-[235px] rounded-[5px] overflow-hidden mt-8">
    <Display value="1000" />
    <Button label="AC" triple @onCalcButtonClick="clearMemory" />
    <Button label="/" operation @onCalcButtonClick="setOperation" />
    <Button label="7" @onCalcButtonClick="addDigit" />
    <Button label="8" @onCalcButtonClick="addDigit" />
    <Button label="9" @onCalcButtonClick="addDigit" />
    <Button label="*" operation @onCalcButtonClick="setOperation" />
    <Button label="4" @onCalcButtonClick="addDigit" />
    <Button label="5" @onCalcButtonClick="addDigit" />
    <Button label="6" @onCalcButtonClick="addDigit" />
    <Button label="-" operation @onCalcButtonClick="setOperation" />
    <Button label="1" @onCalcButtonClick="addDigit" />
    <Button label="2" @onCalcButtonClick="addDigit" />
    <Button label="3" @onCalcButtonClick="addDigit" />
    <Button label="+" operation @onCalcButtonClick="setOperation" />
    <Button label="0" double @onCalcButtonClick="addDigit" />
    <Button label="." @onCalcButtonClick="addDigit" />
    <Button label="=" operation @onCalcButtonClick="setOperation" />
  </div>
</template>

<script>
import Button from '@/components/Button.vue';
import Display from '@/components/Display.vue';
export default {
  methods: {
    clearMemory() {
      console.log('Cleaning Memory')
    },
    setOperation(operator) {
      console.log('Operator', operator)
    },
    addDigit(digit) {
      console.log('Digit', digit)
    }
  },
  components: {
    Button,
    Display
  },
}
</script>
<style scoped>
.calculator {
  display: grid;
  grid-template-columns: repeat(4, 25%);
  grid-template-rows: 1fr 48px 48px 48px 48px 48px;
}
</style>