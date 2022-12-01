<template>
  <div class="calculator h-[320px] w-[235px] rounded-[5px] overflow-hidden mt-8">
    <Display :value="displayValue" />
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
  data() {
    return {
      displayValue: "0",
      clearDisplay: false,
      operation: null,
      values: [0, 0],
      current: 0
    }
  },
  methods: {
    clearMemory() {
      Object.assign(this.$data, this.$options.data())
    },
    setOperation(operator) {
      if (this.current === 0) {
        this.operation = operator
        this.current = 1
        this.clearDisplay = true
      } else {
        const equals = operator === '='
        const currentOperation = this.operation

        try {
          this.values[0] = eval(
            `${this.values[0]} ${currentOperation} ${this.values[1]}`
          )
        } catch (e) {
          this.$emit('onError', e)
        }

        this.values[1] = 0
        this.displayValue = this.values[0]
        this.operation = equals ? null : operator
        this.current = equals ? 0 : 1
        this.clearDisplay = !equals
      }
      // console.log('Operator', operator)
    },
    addDigit(d) {
      if (d === '.' && this.displayValue.includes('.')) return
      const clearDisplay = this.displayValue === '0' || this.clearDisplay
      const currentValue = clearDisplay ? "" : this.displayValue
      const displayValue = currentValue + d

      this.displayValue = displayValue
      this.clearDisplay = false

      if (d !== '.') {
        const curr = this.current
        const newValue = parseFloat(displayValue)
        this.values[curr] = newValue
      }
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