<script setup>
import Mybar from './components/Mybar.vue';
import Mycard from './components/Mycard.vue';
import { ref, onMounted } from 'vue';

// Define a ref for storing fetched items
const Items = ref([]);

// Fetch items from the API when the component is mounted
onMounted(async () => {
  try {
    const response = await fetch('https://www.melivecode.com/api/attractions');
    if (!response.ok) {
      throw new Error('Failed to fetch items');
    }
    const data = await response.json();
    Items.value = data;
  } catch (error) {
    console.error(error);
  }
});
</script>

<template>
  <header>
    <Mybar />
  </header>
  <main>
    <div class="grid-container">
      <Mycard v-for="item in Items" v-bind="item" />
    </div>
  </main>
</template>

<style scoped>
.grid-container {
  display: grid;
  grid-column-gap: 0.5rem;
  grid-row-gap: 0.5rem;
}

@media (min-width: 576px) {
  .grid-container {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (min-width: 992px) {
  .grid-container {
    grid-template-columns: repeat(3, 1fr);
  }
}
</style>
