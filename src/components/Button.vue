<template>
  <button class="bg-[#f0f0f0] border border-r-[#888] border-b-[#888] text-[1.4em] text-gray-600 outline-0 font-mono"
    :class="{ double, triple, operation }" @click="$emit('onCalcButtonClick', label)">
    {{ label }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    label: {},
    operation: { type: Boolean },
    double: { type: Boolean },
    triple: { type: Boolean }
  },
}
</script>

<style scoped>
.double {
  @apply col-span-2
}

.triple {
  @apply col-span-3
}

.operation {
  @apply bg-[#fa8231] text-white;
}

.operation:active {
  @apply bg-[#fa8231cc]
}
</style>