<script setup lang="ts" defer>
import { ref } from 'vue';
import { Person } from '../types/person';

const person = ref<Person>({
  name: "",
  age: 0,
});

const emits = defineEmits<{
  (e: "submit", name: string, age: number): void;
}>();

const onSubmit = (name: string, age: number) => {
  emits("submit", name, age);
  person.value = {
    name: "",
    age: 0,
  };
}

</script>

<template>
  <form id="form_container" @submit.prevent="() => onSubmit(person.name, person.age)">
    <div id="input_area">
      <div class="input_area">
        <label>name:</label>
        <input v-model="person.name" type="text" />
      </div>
      <div class="input_area">
        <label>age:</label>
        <input v-model="person.age" type="number" />
      </div>
    </div>
    <div id="buttun_wrapper">
      <button id="regist_button" type="submit">register</button>
    </div>
  </form>
</template>

<style scoped>
#form_container {
  background-color: rgba(245, 183, 113, 0.168);
  height: 10rem;
  width: 40%;
  margin: 1rem auto;
  padding: 2rem;
  border-radius: 5px;
}
#input_area {
  width: 100%;
  /* margin: 0 auto; */
}
.input_area {
  width: 35%;
  margin: 1rem auto;
  display: flex;
  justify-content: space-between;
  height: 2rem;
  align-items: baseline;
  label {
    font-weight: bold;
  }
  input {
    height: 1.5rem;
    border-radius: 3px;
    width: 50%;
    padding: 3%;
    font-size: medium;
    appearance: auto !important;
  }
}
#buttun_wrapper {
  width: 100%;
}
#regist_button {
  margin-top: 0.5rem;
  width: 20%;
  height: 2rem;
  font-size: large;
  font-weight: bold;
  background-color: rgb(243, 239, 157);
  border-radius: 5px;
  cursor: pointer;
  box-shadow: 3px 3px 3px 1px rgba(0,0,0,0.5);
}
#regist_button:active {
  background-color: rgb(235, 234, 212);
  box-shadow: 2px 2px 3px 1px rgba(0,0,0,0.5);
}
</style>