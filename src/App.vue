<template>
  <div class="app">
    
    <button @click="showList = !showList">
      {{ showList ? 'Скрыть список' : 'Показать список' }}
    </button>

 
    <ul v-if="showList">
      <li class="li_list"
        v-for="(user, index) in users"
        :key="index"
        @mouseenter="hoverIndex = index"
        @mouseleave="hoverIndex = null"
        :style="{ color: hoverIndex === index ? 'red' : 'black' }"
      >
       
        {{ user.name }}

        
        <button @click="toggleInfo(index)">
          {{ user.showInfo ? 'Скрыть' : 'Показать' }} возраст
        </button>
        <span v-if="user.showInfo"> — {{ user.age }} лет</span>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const showList = ref(true);
const hoverIndex = ref(null);

const users = ref([
  { name: 'Алексей', age: 28, showInfo: false },
  { name: 'Мария', age: 34, showInfo: false },
  { name: 'Иван', age: 22, showInfo: false }
]);

const toggleInfo = (index) => {
  users.value[index].showInfo = !users.value[index].showInfo;
};
</script>

<style scoped>
.app {
  font-family: Arial, sans-serif;
}

button {
  margin-left: 10px;
  cursor: pointer;
}

.li_list {
  margin: 0 25px 0 25px;
} 
</style>