<script setup lang="ts">
import { Person } from '../types/person';

const props = defineProps<{
  person: Person,
}>();

const emits = defineEmits<{
  (e: "delete", name: string): void;
}>();

const onDelete = (name: string) => {
  emits("delete", name);
}
</script>

<template>
  <div class="person">
    <span>{{ props.person.name }}</span>
    <span>age:{{ props.person.age }}</span>
    <button @click="() => onDelete(person.name)">delete</button>
  </div>
</template>

<style scoped>
.person {
  background-color: #b49518;
  width: 60%;
  display: flex;
  justify-content: space-between;
  margin: 0.5rem;
  padding: 15px 20px;
  border-radius: 5px;
  align-items: baseline;
}
span {
  font-weight: 700;
}
button {
  padding: 5px 10px;
  font-size: medium;
  font-style: initial;
  font-weight: bold;
  border-radius: 5px;
  border-width: 1px;
}
</style>