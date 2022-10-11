<template>
  <div>
    <div>Home page</div>
    <h1>{{ msg }}</h1>
    <h1>Made By Getters</h1>
    <div v-for="gettersUser in getUsers" :key="gettersUser.id">
      {{ gettersUser.id }} {{ gettersUser.name }} 
    </div>
    
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from "vue";
import { useStore } from "vuex";

const store = useStore();
const msg = ref("Welcome to my Vuex Store");

const getUsers = computed(() => {
  return store.getters.getUsers;
});

onMounted(() => {
  // dispatch the fetchUsers action which commits a mutation to update the state
  store.dispatch("fetchUsers");
});
</script>
