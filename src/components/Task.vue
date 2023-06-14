<script setup>
import { defineProps } from 'vue';

const { task } = defineProps(["task"]);

const thisTask = task.task;
</script>

<template>
    <div class="task_container">
        <div class="task_header">
            <div class="task_id">
                <p>#{{ thisTask.id }}</p>
            </div>
            <div class="task_type">
                <p>{{ thisTask.taskType }}</p>
            </div>
        </div>
        <p class="task_address">{{ thisTask.address }}</p>
        <p class="task_phone">{{ thisTask.phone }}</p>
    </div>
</template>

<style scoped>

.task_container {
    width: 85%;
    padding: 1rem 1.5rem;
    margin-top: 1rem;
    background: #FFFFFF;
    border: 1px solid #E7EBFB;
    box-shadow: 0px 8px 16px rgba(105, 132, 230, 0.08);
    border-radius: 16px;
    cursor: pointer;
}

.task_header {
    display: flex;
    align-items: center;
    height: 2rem;

    font-family: 'Lato', sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 15px;
    line-height: 16px;
    letter-spacing: 0.0048em;

    color: #27265A;
}


.task_id {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #E7EBFB;
    width: 2rem;
    height: 1.8rem;
    padding: 0 0.3rem;
    border-radius: 8px;
}

.task_type {
    display: flex;
    justify-content: center;
    align-items: center;

    background: #D0F4FF;
    border-radius: 8px;
    height: 1.8rem;
    padding: 0 0.5rem;
    margin-left: .7rem;
}

.task_address {
    height: 1rem;

    font-family: 'Lato', sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 18px;
    line-height: 24px;
    letter-spacing: 0.0048em;

    color: #27265A;

    margin: 1rem 0;
}

.task_phone {
    height: 1rem;

    font-family: 'Lato';
    font-style: normal;
    font-weight: 400;
    font-size: 18px;
    line-height: 24px;
    letter-spacing: 0.0048em;

    color: #A09DA7;
    margin: 1rem 0;
}
</style>