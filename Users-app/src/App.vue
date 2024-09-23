<script setup lang="ts">
import { ref } from 'vue';
import UserCard from './components/user-card.vue';
import user1Photo from './assets/user1.jpg';
import user2Photo from './assets/user2.png';
import user3Photo from './assets/user3.jpg';
import user4Photo from './assets/user4.jpg';
import user5Photo from './assets/user5.jpeg';
import user6Photo from './assets/user6.jpg';
import user7Photo from './assets/user7.jpg';
import user8Photo from './assets/user8.jpg';
import user9Photo from './assets/user9.jpg';
import user10Photo from './assets/user10.jpg';

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
  },
  {
  firstName: 'Alice',
  lastName: 'Johnson',
  gender: 'Female',
  age: 16,
  position: 'Product Manager',
  photo: user3Photo,
  hobbies: ['Photography', 'Yoga'],
  },
  {
    firstName: 'Bob',
    lastName: 'Brown',
    gender: 'Male',
    age: 32,
    position: 'Data Scientist',
    photo: user4Photo,
    hobbies: ['Data Analysis', 'Hiking'],
  },
  {
    firstName: 'Charlie',
    lastName: 'Davis',
    gender: 'Male',
    age: 17,
    position: 'Web Developer',
    photo: user5Photo,
    hobbies: ['Gaming', 'Cooking'],
  },
  {
    firstName: 'Eve',
    lastName: 'White',
    gender: 'Female',
    age: 22,
    position: "Teacher",
    photo: user6Photo,
    hobbies: ['Writing', 'Running'],
  },
  {
    firstName: 'David',
    lastName: 'Wilson',
    gender: 'Male',
    age: 29,
    position: 'Network Engineer',
    photo: user7Photo,
    hobbies: ['Networking', 'Gaming'],
  },
  {
    firstName: 'Mia',
    lastName: 'Taylor',
    gender: 'Female',
    age: 16,
    position: 'Content Writer',
    photo: user8Photo,
    hobbies: ['Blogging', 'Cooking'],
  },
  {
    firstName: 'Tom',
    lastName: 'Anderson',
    gender: 'Male',
    age: 35,
    position: 'Systems Analyst',
    photo: user9Photo,
    hobbies: ['Chess', 'Reading'],
  },
  {
    firstName: 'Emma',
    lastName: 'Thomas',
    gender: 'Female',
    age: 26,
    position: 'UX Researcher',
    photo: user10Photo,
    hobbies: ['Usability Testing', 'Sketching'],
  },
]);

const filteredUsers = ref<User[]>(users.value);
const message = ref('');

const filterGender = (gender: string) => {
  if (gender === 'female' || gender === 'male') {
    filteredUsers.value = users.value.filter(user => user.gender.toLowerCase() === gender.toLowerCase());
    message.value = filteredUsers.value.length === 0 ? `Немає користувачів статі ${gender}` : '';
  } else {
    filteredUsers.value = users.value;
    message.value = '';
  }
}
</script>

<template>
<div class="toolbar">
  <button class="female btn" @click="filterGender('female')">Female</button>
  <button class="male  btn" @click="filterGender('male')" >Male</button>
</div>
<div class="user-container">
    <UserCard v-for="(user, index) in filteredUsers" :key="index" :user="user"></UserCard>
</div>
<p v-if="message" class="error">{{ message }}</p>
</template>

<style scoped>
.user-container{
  display: flex;
  flex-wrap: wrap;
  gap: 20px; 
  padding: 20px; 
  margin: 0 auto;
  width: auto;
  
}
.toolbar{
  margin: auto;
  border: 1px solid rgb(243, 238, 234);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px;
  width: 400px;
  border-radius: 20px;
  background-color: rgb(243, 238, 234);
}

.btn{
  width: 100px;
  margin: 3px;
  height: 30px;
  color: white;
  font-weight: bold;
  border: none;
}

.female{
  background-color: rgb(248, 140, 248);
}

.male{
  background-color: rgb(105, 167, 243);
}

.error {
  color: rgb(0, 0, 0);
  text-align: center;
  margin-top: 20px;
  font-weight: bold;
}
</style>
