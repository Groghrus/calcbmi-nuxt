<template>
  <div class="grid grid-cols-2 gap-2 mb-6 text-center">
    <div class="rounded-md shadow-md bg-gray-800 p-4 w-full">
      <p class="uppercase font-bold">Вес</p>
      <p class="text-5xl font-bold">{{ weight }}</p>
      <div class="flex items-center justify-around">
        <button
          @click="upWeight(-1)"
          class="rounded-full bg-gray-900 h-12 w-12 text-2xl">-</button>
        <button
          @click="upWeight(1)"
          class="rounded-full bg-gray-900 h-12 w-12 text-2xl">+</button>
      </div>
    </div>
    <div class="rounded-md shadow-md bg-gray-800 p-4 w-full">
      <p class="uppercase font-bold">Возраст</p>
      <p class="text-5xl font-bold">{{ age }}</p>
      <div class="flex items-center justify-around">
        <button
          @click="upAge(-1)"
          class="rounded-full bg-gray-900 h-12 w-12 text-2xl"
        >-</button>
        <button
          @click="upAge(1)"
          class="rounded-full bg-gray-900 h-12 w-12 text-2xl"
        >+</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'weight',
  data() {
    return {
      age: 10,
      weight: 30
    };
  },
  methods: {
    upAge(value) {
      this.age += value
      this.$emit('awListener', {age: this.age, weight: this.weight})
    },
    upWeight(value) {
      this.weight += value
      this.$emit('awListener', {age: this.age, weight: this.weight})
    }
  }
};
</script>

<style scoped>

</style>
