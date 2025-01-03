<script setup lang="ts">
import { ref } from 'vue';
import { Person } from '../types/person';
import PersonListComponent from './PersonList.vue';
import PersonForm from './PersonForm.vue';

const tempPersons = ref<Person[]>([]);

const onSubmit = (name: string, age: number) => {
  if (name && age !== 0) {
    tempPersons.value = [
      ...tempPersons.value,
      {
        name,
        age,
      }
    ];
  }
};

const onDelete = (name: string): void => {
  tempPersons.value = tempPersons.value.filter((person) => person.name !== name);
};
</script>

<template>
  <h1 id="title">Vue登録テスト</h1>
  <div class="container">
    <PersonForm @submit="onSubmit" />
    <PersonListComponent :persons="tempPersons" @delete="onDelete" />
  </div>
</template>

<style scoped>
#title {
  width: 90%;
  background-color: rgb(182, 248, 226);
  padding: 2rem;
  margin: 1rem auto;
}
</style>