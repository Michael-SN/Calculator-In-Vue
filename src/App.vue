<template>
  <div>
    <h2 class="text-2xl text-center font-mono">The Calculator</h2>
    <Calculator />
  </div>
</template>

<script>
import Calculator from '@/views/Calculator.vue';

export default {
  components: {
    Calculator,
  },
}
</script>