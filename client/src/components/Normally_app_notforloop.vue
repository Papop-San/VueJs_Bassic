<script setup>
import Mybar from './components/Mybar.vue';
import Mycard from './components/Mycard.vue'
import Items from './assets/attraction.json'
</script>

<template>
  <header>
    <Mybar />
  </header>
  <main>
    <!-- We use for get variable from json file -->
    <!-- v-bind:class="Items[0] -->
    <div class="grid-container">
      <Mycard v-bind="Items[0]"/>
      <Mycard v-bind="Items[1]"/>
      <Mycard v-bind="Items[2]"/>
      <Mycard v-bind="Items[3]"/>
      <Mycard v-bind="Items[4]"/>
      <Mycard v-bind="Items[5]"/>
    </div>
  </main>

</template>

<style scoped>
  .grid-container{
    display:  grid;
    grid-column-gap:0.5rem ;
    grid-row-gap: 0.5rem ;
  }

  @media (min-width: 576px) {
    .grid-container {
        grid-template-columns: repeat(3, 1fr); 
    }
  
    @media (min-width: 992px){
      .grid-container{
        grid-template-columns: repeat(3,1fr);
      }
    }
}
</style>
