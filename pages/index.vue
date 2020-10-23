<template>
  <div class="container mx-auto px-4 pt-6 max-w-lg">
      <gender @genderListener="saveGender"/>
      <height @heightListener="saveHeight"/>
      <weight @awListener="saveAgeWeigh"/>
      <button
        @click="calculateBMI"
        class="bg-blue-600 font-bold uppercase p-4 fixed w-full bottom-0 left-0">
        Расчитайте ваш индекс BMI
      </button>
  </div>
</template>

<script>
import Gender from '~/components/home/gender';
import Height from '~/components/home/height';
import Weight from '@/components/home/weight';
export default {
  components: {
    Weight,
    Height,
    Gender
  },
  data() {
    return {
      gender: "male",
      height: 120,
      age: 10,
      weight: 30
    };
  },
  methods: {
    saveGender(value) {
      this.gender = value
    },
    saveHeight(value) {
      this.height = value
    },
    saveAgeWeigh(value) {
      this.age = value.age
      this.weight = value.weight
    },
    calculateBMI() {
      let val = this.height / 100
      const bmi = this.weight / (val * val)
      this.$router.push({
        query: {bmi: bmi.toFixed(2)},
        path: '/result'
      })
    }
  }

}
</script>

<style>



</style>
