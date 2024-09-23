<script setup lang="ts">
interface UserData {
  firstName: string;
  lastName: string;
  gender: string;
  age: number;
  position: string;
  photo: string;
  hobbies: string[];
}

const props = defineProps<{
  user: UserData
}>();
</script>

<template>
<div :class="{'young-user': user.age <= 18, 'adult-user': user.age > 18}" class="user-card">
    <img :src="user.photo" alt="User Photo" class="user-photo" />
    <span class="name-username">{{ user.firstName }} {{ user.lastName }}</span>
    <span class="gender">{{ user.gender }}</span>
    <span class="position">{{ user.position }}</span>
    <span v-for="hobby in user.hobbies" :key="hobby" class="hobbies">{{ hobby }}</span>
    <span v-if="user.age > 18" class="age">{{ user.age }} y.o.</span>
</div>
</template>

<style scoped>
.user-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5px;
  background-color: #f5f5f5;
  border-radius: 10px;
  padding: 10px;
  width: 240px;
  height: auto;
  margin: 20px auto;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}

.user-photo{
  width: 80px;
  height: 80px;
  border-radius: 50%;
}

.name-username{
  font-size: 18px;
  font-weight: bold;
}

.young-user{
  border: 1.5px solid rgb(27, 236, 229);
}

.adult-user{
  border: 1.5px solid rgb(236, 149, 27);
}
</style>
