<script setup lang="ts">
import { ref } from 'vue';
import UserCard from './components/user-card.vue';
import user1Photo from './assets/user1.jpg';
import user2Photo from './assets/user2.png';

interface User {
  firstName: string;
  lastName: string;
  gender: string;
  age: number;
  position: string;
  photo: string;
  hobbies: string[];
}

const users = ref<User[]>([
  {
    firstName: 'John',
    lastName: 'Doe',
    gender: 'Male',
    age: 30,
    position: 'Software Developer',
    photo: user1Photo,
    hobbies: ['Coding', 'Reading', 'Gaming'],
  },
  {
    firstName: 'Jane',
    lastName: 'Smith',
    gender: 'Female',
    age: 25,
    position: 'Designer',
    photo: user2Photo,
    hobbies: ['Drawing', 'Traveling'],
  }
]);
</script>

<template>
<div class="user-container">
    <UserCard v-for="(user, index) in users" :key="index" :user="user"></UserCard>
</div>
</template>

<style >
</style>
