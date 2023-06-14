<script setup>

import search_icon from '../public/search.png';
import filter_icon from '../public/link.png';
import sort_icon from '../public/sort.png';
import show_icon from '../public/link1.png';
import join_icon from '../public/link2.png';

</script>

<template>
    <div class="search_container">
        <div class="search_bar">
            <img class="search_icon" :src="search_icon"/>
            <input class="search_field" name="searchField" placeholder="Найти обращение" />
        </div>
        <div class="search_options">
            <button class="search_option">
                <img class="filter_icon" :src="filter_icon"/>
                <h3 class="filter_text filter">
                    Фильтровать
                </h3>
            </button>
            <button class="search_option">
                <img class="filter_icon" :src="sort_icon" />
                <h3 class="filter_text">
                    Сначала новые
                </h3>
            </button>
            <button class="search_option">
                <img class="filter_icon" :src="show_icon" />
                <h3 class="filter_text">
                    Показывать
                </h3>
            </button>
            <button class="search_option">
                <img class="filter_icon" :src="join_icon" />
                <h3 class="filter_text">
                    Обьединять
                </h3>
            </button>
        </div>
    </div>
</template>

<style scoped>

.search_container {
    position: fixed;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: #F8F7FD;
    height: 3.5rem;
    width: 100%;
    margin-top: 6.2rem;
    margin-bottom: 2rem;
}

.search_bar {
    height: 100%;
    margin-left: 3rem;
    display: flex;
    align-items: center;
    justify-content: start;
}

.search_field {
    margin-left: .7rem;
    background-color: #F8F7FD;
    border: none;

    font-family: 'Lato', sans-serif;
    font-weight: 300;
    font-size: 17px;
    line-height: 24px;
    letter-spacing: 0.03em;
    color: rgba(160, 157, 167, 1);
}

.search_options {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 45%;
    margin-top: 1rem;
    margin-right: 4.5rem;
}

.search_option {
    display: flex;
    align-items: center;
    background-color: inherit;
    border: none;
    margin-bottom: 1rem;
    cursor: pointer;
}

.filter_text {
    margin-left: .5rem;
    font-family: 'Lato', sans-serif;
    font-weight: 200;
    font-size: 17px;
    line-height: 24px;
    letter-spacing: 0.03em;
    color: rgba(105, 132, 230, 1);
} 

.filter {
    color: #000;
}

</style>