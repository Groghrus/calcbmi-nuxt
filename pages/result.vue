<template>
  <div class="container mx-auto px-4 pt-6 max-w-lg">
     <p class="text-4xl font-bold mb-4">Ваш результат</p>
    <div class="rounded bg-gray-700 p-6 text-center">
      <p class="text-green-400 font-bold uppercase">{{ result.label }}</p>
      <p class="text-6xl font-bold text">{{bmi || '27'}}</p>
      <p class="text-gray-400 font-bold">{{ result.label }} BMI</p>
      <p class="text-2xl font-bold">{{ result.range }}</p>
      <p class="my-8 text-xl">{{ result.message }}</p>
      <button
        class="my-4 bg-gray-600 p-4 rounded w-full uppercase"
        @click="share"
      >Поделиться</button>
    </div>
    <nuxt-link to="/" class="bg-red-600 font-bold uppercase text-center p-4 fixed w-full bottom-0 left-0">
      Пересчитайте ваш индекс BMI
    </nuxt-link>
  </div>
</template>

<script>
export default {
  name: 'result',
  data() {
    return {
      bmi: this.$route.query.bmi,
      type: {
        underweight: {
          label: "Низкий вес",
          range: "<18.5",
          message: "Кажется, у вас недостаточный вес для вашего роста"
        },
        normal: {
          label: "Нормальный",
          range: "18.5 - 24.9",
          message: "У вас нормальная масса тела. Молодец!"
        },
        overweight: {
          label: "Избыточный вес",
          range: "25.0 - 29.9",
          message: "Вы набираете вес!"
        },
        obese1: {
          label: "Ожирение 1 стадия",
          range: "30.0 - 34.9",
          message: "Время пойти в спортзал"
        },
        obese2: {
          label: "Ожирение 2 стадия",
          range: "35.0 - 39.9",
          message: "Время задуматься о вашем весе всерьез"
        },
        obese3: {
          label: "Ожирение 3 стадия",
          range: ">40",
          message: "Это очень тревожное состояние."
        }
      }
    };
  },
  methods: {
    share() {
      if (navigator.share) {
        navigator
          .share({
            title: `Мой BMI ${this.bmi}`,
            text: 'Индекс массы тела'
          })
          .then(() => console.log('Successful share'))
          .catch(error => console.log('Error sharing', error))
      } else {
        alert('Sharing is not allowed in this device')
      }
    }
  },
  computed: {
    result() {
      if (this.bmi >= 40) {
        return this.type.obese3;
      }
      if (this.bmi <= 39.99 && this.bmi >= 35) {
        return this.type.obese2;
      }
      if (this.bmi <= 34.99 && this.bmi >= 30) {
        return this.type.obese1;
      }
      if (this.bmi <= 29.99 && this.bmi >= 25) {
        return this.type.overweight;
      }
      if (this.bmi <= 18.5 && this.bmi >= 24.99) {
        return this.type.normal;
      }
      if (this.bmi < 18.5) {
        return this.type.underweight;
      }
      return this.type.normal;
    }
  }
}
</script>

<style>

</style>
