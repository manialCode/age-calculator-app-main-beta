<script setup>
  import { ref } from "vue";

  const uno = ref(1);

  const emit = defineEmits(["save-date"]);
  const send = (number) => {
    emit("save-date", number);
    console.log(number);
    // console.log(inputDate.value);
  };
</script>

<template>
  <form>
    <div class="grid-layout fs-500">
      <div class="input-box">
        <label for="day" class="fs-300 text-neutral-700 fw-extra-bold"
          >DAY</label
        >
        <input
          class="fw-extra-bold bg-neutral-100 text-neutral-900"
          placeholder="DD"
          type="number"
          name="day"
          id="day" />
        <span class="feedback hidden">This field is required</span>
      </div>
      <div class="input-box">
        <label for="month" class="fs-300 text-neutral-700 fw-extra-bold"
          >MONTH</label
        >
        <input
          class="fw-extra-bold bg-neutral-100 text-neutral-900"
          placeholder="MM"
          type="number"
          name="month"
          id="month" />
      </div>
      <div class="input-box">
        <label for="year" class="fs-300 text-neutral-700 fw-extra-bold"
          >YEAR</label
        >
        <input
          class="fw-extra-bold bg-neutral-100 text-neutral-900"
          placeholder="YYYY"
          type="number"
          name="year"
          id="year" />
      </div>
    </div>
    <div class="button">
      <button
        type="submit"
        @click="send(uno)"
        @keypress.enter="send(uno)"
        class="bg-primary-400">
        <img src="./icons/icon-arrow.svg" alt="row" />
      </button>
    </div>
  </form>
</template>

<style lang="scss" scoped>
  .grid-layout {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
  }
  form .input-box {
    display: flex;
    flex-direction: column;
  }
  form .input-box > input {
    border: 1px solid $clr-neutral-500;
    border-radius: 0.5rem;
    padding: 0.45rem;
    width: 100%;
  }
  form .input-box > input {
    text-indent: 0.4rem;
  }
  form .input-box > input:focus-visible,
  form .input-box > input:focus,
  form .input-box > input:focus-within {
    border: 1px solid $clr-primary-400;
    cursor: pointer;
    outline: none;
  }

  form .input-box > input::placeholder {
    letter-spacing: 0.5px;
  }

  form .input-box > label {
    text-align: left;
    letter-spacing: 0.1rem;
    font-size: 0.55rem;
    margin-bottom: 0.5em;
  }

  .button {
    width: 100%;
    position: relative;
    z-index: 1;
  }

  .button button[type="submit"] {
    border: none;
    padding: 1rem;
    margin: 1rem 0;
    border-radius: 50%;
    z-index: 2;
    transition: all 0.5s ease;
  }

  .button button[type="submit"]::before {
    content: "";
    position: absolute;
    top: 50%;
    left: 0;
    width: 100%;
    border: 1px solid $clr-neutral-500;
    z-index: -1;
  }
  .button button[type="submit"]:hover {
    cursor: pointer;
    background-color: $clr-neutral-900;
  }
  .button button[type="submit"] img {
    width: 1.25rem;
  }

  @media (min-width: 30em) {
    .grid-layout {
      grid-template-columns: repeat(4, 1fr);
    }

    .button button[type="submit"] {
      margin: 0.55rem 0;
    }
    .button {
      text-align: right;
    }
  }

  .err .input-box > label,
  .err .input-box > .feedback {
    color: $clr-accent-100;
  }
  .err .input-box > input {
    border: 1px solid $clr-accent-100;
  }
  .feedback {
    margin-top: 0.1rem;
    font-size: 0.5rem;
    font-style: italic;
  }

  .feedback.hidden {
    display: none;
  }
</style>
