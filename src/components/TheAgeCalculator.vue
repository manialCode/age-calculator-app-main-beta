<script setup>
  import { ref } from "vue";
  import AgeForm from "./AgeForm.vue";
  import CalculatorResult from "./CalculatorResult.vue";

  const userDate = ref({
    day: Number,
    month: Number,
    year: Number,
  });

  const dos = ref(2);
  console.log(dos.value);

  const saveDate = (number) => {
    dos.value = number;
  };
  console.log(dos.value);
  console.log(userDate.value);
</script>

<template>
  <div class="age-container bg-neutral-100">
    <AgeForm v-bind="userDate" @save-date="saveDate" />
    <CalculatorResult :userDate:="userDate" />
  </div>
</template>

<style lang="scss" scoped>
  .age-container {
    padding: 2rem 1rem;
    width: 100%;
    margin: auto;
    border-radius: 5%;
    border-bottom-right-radius: 30%;
  }

  @media (min-width: 28.125em) {
    .age-container {
      width: 490px;
      padding: 2.1rem 2rem;
    }
  }
</style>
