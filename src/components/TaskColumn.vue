<script setup>
import addsquare from '../public/addsquaretask.png';
import arrowsquareleft from '../public/arrowsquarelefttask.png';

import Task from './Task.vue';
import { ref, defineProps } from 'vue';

const { title, tasks, first_row } = defineProps(["title", "tasks", "first_row"]);

const numberOfTasks = tasks.length;
let orders = [...new Set(tasks.map(task => task.orderId))];

let tasksByOrders = ref([]);
let separateTasks = [];

for(let i = 0; i < orders.length; i++){
    const id = orders[i];

    console.log(id)

    if(id == 0) {
        const task = [...tasks.filter(task => task.orderId == id)]
        separateTasks.push(task);
    } else {
        const orderTasks = {
            orderId: id,
            tasks: [...tasks.filter(task => task.orderId == id)],
            collapsed: false
        };
        tasksByOrders.value.push(orderTasks);
    }
}

let column_collapsed = ref(false);

</script>

<template>
    <div class="column">
        <header :class="['column_header', column_collapsed ? 'column_collapsed' : 'column_expanded']">
            <div class="column_title_container">
                <h2 class="column_title">{{ title }}</h2>
                <p class="column_number_of_tasks">( {{ numberOfTasks }} )</p>
            </div>
            <div class="column_header_options">
                <img v-if="first_row" :src="addsquare" class="header_option add_option">
                <button class="header_option" @click="column_collapsed = !column_collapsed">
                    <img :src="arrowsquareleft"/>
                </button>
            </div>
        </header>
        <div v-if="!column_collapsed">
            <div v-for="order in tasksByOrders" :key="order.orderId" class="main_container">
            <div class="order_container">
                <div class="order_header">
                    <h2 class="order_title">Заявка #{{ order.orderId }}</h2>
                    <button class="header_option order_collapse" @click.prevent="order.collapsed = !order.collapsed">
                        <img :src="arrowsquareleft">
                    </button>
                </div>
                <div v-if="!order.collapsed">
                    <div v-for="task in order.tasks" :key="task.id">
                        <Task :task="{task}" :orderItem="true"/>
                    </div>
                </div>
            </div>
            </div>
            <div v-for="task in separateTasks[0]" :key="task.id">
                <Task :task="{task}" :orderItem="false"/>
            </div>
        </div>
    </div>
</template>

<style scoped>

.column_header {
    display: flex;
    align-items: center;

    background-color: rgba(248, 247, 253, 1);
}

.column_expanded {
    justify-content: space-between;

    width: 21rem;
    height: 3.25rem;
    margin-bottom: 1.5rem;
    border-radius: 24px 24px 8px 8px;
}

.column_collapsed {
    justify-content: end;
    width: 40rem;
    height: 6rem;
    border-radius: 24px;
    margin: 0 -17.5rem;
    
    transform: rotate(-90deg);
    margin-top: 17rem;
}

.column_title_container {
    display: flex;
    align-items: center;
    margin: 0 1.5rem;
}

.column_title {
    font-family: 'Lato', sans-serif;
    font-style: normal;
    font-weight: 500;
    font-size: 18px;
    line-height: 24px;
    letter-spacing: 0.0048em;

    color: #544F5E;
}

.column_number_of_tasks {
    font-family: 'Lato', sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 18px;
    line-height: 24px;
    letter-spacing: 0.0048em;

    margin-left: .8rem;

    color: #A09DA7;
}

.column_header_options {
    margin-right: 1rem;
    display: flex;
    justify-content: end;
    align-items: center;

    cursor: pointer;
}

.header_option {
    all: unset;
    width: 1.5rem;
    height: 1.5rem;
    
}

.add_option {
    margin-right: .5rem;
}


/* Order styles */

.order_container {
    width: 19rem;
    border-radius: 16px;
    padding: 1rem 1rem;
    margin-top: 1rem;
    background-color: rgba(248, 247, 253, 1);
}

.order_header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: -.2rem 0.5rem;
}

.order_title {
    font-family: 'Lato', sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 20px;
    line-height: 24px;
    letter-spacing: 0.0048em;

    color: #544F5E;
}

.order_collapse {
    transform: rotate(90deg);
}
</style>