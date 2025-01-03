<script setup lang="ts">
import { Person } from '../types/person';
import PersonComponent from './Person.vue'

const props = defineProps<{
  persons: Person[],
}>();

const emits = defineEmits<{
  (e: "delete", name: string): void;
}>();

const onDelete = (name: string) => {
  emits("delete", name);
}
</script>

<template>
  <div class="container">
    <ul v-if="props.persons.length > 0">
      <li v-for="person in props.persons">
        <PersonComponent :person="person" @delete="onDelete(person.name)" />
      </li>
    </ul>
    <p v-if="props.persons.length === 0" class="not_register">not registered</p>
  </div>
</template>

<style scoped>
.container {
  margin: 0 auto;
  width: 80%;
}
ul {
  background-color: antiquewhite;
  padding: 2rem;
  border-radius: 5px;
}
li {
  list-style: none;
  display: flex;
  justify-content: center;
}
.not_register {
  background-color: rgb(242, 155, 155);
  padding: 2rem;
  font-size: large;
  font-weight: bold;
  border-radius: 5px;
}
</style>