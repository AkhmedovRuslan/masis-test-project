<script setup>
import header_mode_view_1 from '../public/Header_mode_view_1.png';
import header_mode_view_2 from '../public/Header_mode_view_2.png';
import map_icon from '../public/map1.png';
import add_icon from '../public/addsquare.png';

</script>

<template>
    <header class="header_container">
        <div class="header_flex_container">
            <div class="header_title_container">
                    <h1 class="header_title">
                        Обращения
                    </h1>
                <div class="header_view_modes">
                    <button class="button view_mode_button">
                        <img class="view_button_icon" :src="header_mode_view_1"/>
                    </button>
                    <div class="delimiter"></div>
                    <button class="button view_mode_button">
                        <img class="view_button_icon" :src="header_mode_view_2"/>
                    </button>
                </div>
            </div>
        <div class="header_buttons">
            <button class="button header_button header_button_active">
                <img class="button_icon" :src="add_icon"/>
                <h3 class="button_text">Создать</h3>
            </button>
            <button class="button header_button">
                <img class="button_icon" :src="map_icon"/>
                <h3 class="button_text">Карта</h3>
            </button>
        </div>
        </div>
    </header>
</template>

<style scoped>
.header_flex_container{
    display: flex;
    justify-content: space-between;
    width: 100%;
    height: 5rem;
    margin-top: .8rem;
}

.header_title_container{
    margin-left: 3rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 19rem;
}

.header_title {
    font-family: 'Lato', sans-serif;
    font-weight: 400;
}

.header_view_modes {
    width: 5rem;
    height: 3rem;
    display: flex;
    align-items: center;
    justify-content: space-around;
    padding: 0 0.2rem;

    border: 1px solid #E7EBFB;

    box-shadow: 0px 8px 16px rgba(105, 132, 230, 0.08);
    border-radius: 16px;
}

.delimiter {
    content: "";
    width: 1px;
    height: 100%;
    background: #E7EBFB;
}

.button {
    border: none;
    background-color: inherit;
    cursor: pointer;
}

.view_mode_button {
    height: 2rem;
    width: 2rem;
    display: flex;
    justify-content: center;
    align-items: center;
}

.header_buttons {
    margin-right: 4rem;
    display: flex;
    align-items: center;
    justify-content: space-around;
    width: 21rem;
}

.header_button {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding: 8px 20px;
    height: 2.7rem;


    color: #000;
    background-color: #fff;
    border: 1px solid #6985E6;
    border-radius: 12px;
}

.header_button_active {
    background: #6985E6;
    color: #fff;
}

.button_text {
    font-family: 'Lato', sans-serif;
    font-weight: 400;
    font-size: 18px;
    line-height: 24px;
    letter-spacing: 0.03em;
    width: 5rem;
}

.view_button_icon {
    width: 50%;
}

.button_icon {
    width: 25%;
}

</style>