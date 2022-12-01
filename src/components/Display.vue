<template>
  <div class="col-span-4 bg-[#0004] flex items-center justify-end p-[20px] text-[1.6em] font-mono overflow-hidden">
    {{ value }}
  </div>
</template>

<script>
export default {
  name: "Display",
  props: ['value']
}
</script>