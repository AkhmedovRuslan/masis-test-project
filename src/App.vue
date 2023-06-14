<script setup>
import HeaderComponent from './components/HeaderComponent.vue';
import SearchComponent from './components/SearchComponent.vue';
import TaskColumn from './components/TaskColumn.vue';
import Map from "./components/Map.vue";

import {ref, watch} from 'vue';

// request to backend to get columns
import data from './data/tasks.json';
import Menu from './components/Menu.vue';

let columns = ref(data);
const first_row = data.shift();

let collapsed = ref(false);
</script>

<template>
  <div class="app">
    <Menu @collapse="(collapsedVelue) => collapsed = collapsedVelue"/>
    <div :class="['app_view', collapsed ? 'collapsed' : 'expanded']">
      <HeaderComponent/>
      <SearchComponent/>
      <section class="view_container">
        <TaskColumn :title="first_row.title" :tasks="first_row.tasks" :first_row="true" class="column" />
        <div v-for="column in columns" :key="column.id">
          <TaskColumn :title="column.title" :tasks="column.tasks" :first_row="false" class="column" />
        </div>
        <Map/>
      </section>
    </div>
  </div>
</template>

<style>
*{
  padding: 0;
  margin: 0;
  border: 0;
}

.app {
  display: flex;
  height: 100%;
}

.app_view {
  width: 100%;
}

.collapsed {
  margin-left: 0rem;
}

.expanded {
  margin-left: 16rem;
}

.view_container {
  display: flex;
  width: 100%;
  margin-top: 11.5rem;
  margin-left: 2rem;
  gap: 2.5rem;
  align-content: start;
}

@media (min-width: 1024px) {


  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
