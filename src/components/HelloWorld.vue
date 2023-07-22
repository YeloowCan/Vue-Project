<script setup lang="ts">
import { ref, computed, watch } from 'vue';

const count = ref(111);
const list = ref([
  {
    id: 0,
    name: 'huang',
  },
  {
    id: 1,
    name: 'ping',
  },
]);

const increment = () => {
  count.value++;
};

const maxcount = computed(() => {
  return count.value > 120;
});

watch(count, () => {
  list.value.push({
    id: 2,
    name: 'test',
  });
});
</script>

<template>
  <div class="greetings">
    <h1 class="green"></h1>
    <h3 v-if="true">
      {{ count }}
      You’ve successfully created a project with
      <span v-if="maxcount">{{ count }}</span>
      <span v-else>loading</span>
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
    <div v-for="item in list">
      {{ item.name }}
    </div>
  </div>
  <button @click="increment">click</button>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
