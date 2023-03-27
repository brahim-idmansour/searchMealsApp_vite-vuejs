<template>
  <div class="flex flex-col p-8">
    <div class="items-center justify-center">
      <!-- search input -->
    </div>
    <div class="flex justify-center gap-2 mt-2">
      <!-- <pre>{{ letters }}</pre> -->
      <router-link
        :to="{ name: 'byLetter', params: { letter } }"
        v-for="letter of letters"
        :key="letter"
      >
        {{ letter }}
      </router-link>
    </div>
    <!-- <pre>{{ ingredients }}</pre> -->
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from "vue";
import axiosClient from "../axiosClient.js";
// import store from "../store";
// const meals = computed(() => store.state.meals);
const letters = "ABCDEFGHIJKLMNOPQRSTVWXYZ".split("");
const ingredients = ref([]);

onMounted(async () => {
  const response = await axiosClient.get("/list.php?i=list");
  // console.log(response.data);
  ingredients.value = response.data;
});
</script>
