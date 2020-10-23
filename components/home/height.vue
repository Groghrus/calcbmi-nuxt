<template>
  <div class="rounded-md shadow-md bg-gray-800 p-4 mb-6 text-center">
    <p class="uppercase">Рост</p>
    <p class="text-5xl font-bold">
      {{ height }}<small class="text-sm">см</small>
    </p>
    <input
      type="range"
      v-model="height"
      min="120"
      max="215"
      class="slider w-full h-3 rounded-lg outline-none opacity-75 transition-all duration-300 hover:opacity-100"
    >
  </div>
</template>

<script>
export default {
  name: 'height',
  props: {},
  data() {
    return {
      height: 120
    };
  },
  methods: {

  },
  watch: {
    height() {
      this.$emit('heightListener', parseInt(this.height))
    }
  }
};
</script>

<style scoped>

</style>
