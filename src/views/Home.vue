<template>
  <div class="flex flex-col p-8">
    <div class="items-center justify-center">
      <input
        type="text"
        class="rounded border-2 border-gray-200 w-full"
        placeholder="search for meals"
      />
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
  </div>
</template>

<script setup>
import { computed } from "vue";
import store from "../store";

// const meals = computed(() => store.state.meals);
const letters = "ABCDEFGHIJKLMNOPQRSTVWXYZ".split("");
</script>
