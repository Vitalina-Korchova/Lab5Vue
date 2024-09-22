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
<div class="user-card">
    <img :src="user.photo" alt="User Photo" class="user-photo" />
    <h2 class="Name_Username">{{user.firstName }} {{ user.lastName }}</h2>
    <p class="gender">{{ user.gender }}</p>
    <p class="age">{{ user.age }}</p>
    <p class="position">{{ user.position }}</p>
    <p class="hobbies">{{ user.hobbies.join(', ') }}</p>
</div>
</template>

<style scoped>
.user-card {
  display: flex;
  align-items: center;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 10px;
  padding: 20px;
  max-width: 400px;
  margin: 20px auto;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.user-photo{
  width: 50px;
  height: 50px;
  border-radius: 50%;
}
</style>
