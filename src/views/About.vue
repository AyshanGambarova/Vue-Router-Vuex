<template>
  <div>
    <div>About page</div>
    <h1>{{ msg }}</h1>
    <h1>Made By Actions</h1>
    <div v-for="user in users" :key="user.id">
      {{ user.id }} {{ user.name }}
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from "vue";
import { useStore } from "vuex";

const store = useStore();
const msg = ref("Welcome to my Vuex Store");

const users = computed(() => {
  return store.state.users;
});

onMounted(() => {
  // dispatch the fetchUsers action which commits a mutation to update the state
  store.dispatch("fetchUsers");
});
</script>
