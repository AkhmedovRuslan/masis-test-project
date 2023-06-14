<script setup>
import { ref, defineEmits, watch } from 'vue';

import company_icon from '../public/Group.png';
import arrowsquareleft_icon from '../public/arrowsquareleft.png';
import open_menu_icon from "../public/open_menu.png";
import logout_icon from '../public/logout.png';

import phone_icon from '../public/callcalling.png';
import trash_icon from '../public/trash.png';
import notification_icon from '../public/notification.png';

const links = [
    {
        id: 0,
        icon: phone_icon,
        title: "Обращения",
        link: ""
    },
    {
        id: 1,
        icon: trash_icon,
        title: "Архив обращений",
        link: ""
    },
    {
        id: 2,
        icon: notification_icon,
        title: "уведомления",
        link: ""
    }
];

let collapsed = ref(false);
const emit = defineEmits(['collapse']);

watch(collapsed, () => {
    emit("collapse", collapsed.value);
    console.log("emited");
})

</script>

<template>
        <div v-if="collapsed">
            <button class="menu_icon" @click.prevent="collapsed = !collapsed">
                <img :src="open_menu_icon"/>
            </button>
        </div>
        <div v-else>
            <div :class="['menu', collapsed ? 'collapsed' : 'expanded']">
            <header class="menu_header">
                <img class="company_icon" :src="company_icon"/>
                <button class="menu_icon" @click.prevent="collapsed = !collapsed">
                    <img :src="arrowsquareleft_icon"/>
                </button> 
            </header>
            <div class="menu_name_container">
                <hr class="separator"/>
                <h2 class="menu_username">Семён Вишневский</h2>
                <hr class="separator"/>
            </div>
                <div class="menu_links">
                <div v-for="link in links" :key="link.id">
                    <a :href="link.link" class="menu_link">
                        <img class="link_icon" :src="link.icon"/>
                        <h2 class="link_title">{{ link.title }}</h2>
                    </a>
                </div>
            </div>
            <div class="logout_button_container">
                <button class="sign_out">
                    <img class="sign_out_icon" :src="logout_icon"/>
                    <h3 class="sign_out_text">Выйти</h3>
                </button>
            </div>
        </div>
    </div>
</template>

<style scoped>

.menu {
    position: fixed;
    background: #262F3D;
    border-radius: 0px 24px 24px 0px;
    margin-left: 0rem;

    transition: width .3s;
}

.collapsed {
    width: 0rem;
    height: 5rem;
}
.expanded {
    width: 16rem;
    height: 925px;
}

.menu_header {
    display: flex;
    justify-content: space-between;
    margin: 1.5rem 1rem;
    height: 4rem;
}

.company_icon {
    width: 3rem;
    height: 3rem;
    cursor: pointer;
}

.menu_icon {
    all: unset;
    width: 2rem;
    height: 2rem;
    cursor: pointer;
}

.menu_name_container {
    margin-top: 3rem;
}

.menu_username {
    margin: 1.5rem 1.2rem;

    font-family: 'Lato', sans-serif;
    font-style: normal;
    font-weight: 500;
    font-size: 18px;
    line-height: 24px;
    letter-spacing: 0.0048em;

    color: #468FC5;
}

.separator {
    height: 1px;
    background: #FFFFFF;
    opacity: 0.1;
}

.menu_links {
    height: 34.5rem;
    margin: 2rem 1.7rem;
}

.menu_link {
    all: unset;
    cursor: pointer;
    display: flex;
    align-items: center;
    margin-top: .8rem;
}

.link_icon {
    width: 1.9rem;
    height: 1.9rem; 
}

.link_title {
    margin-left: .7rem;
    font-family: 'Lato', sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 15px;
    line-height: 16px;
    letter-spacing: 0.0048em;

    color: #FFFFFF;
}

.logout_button_container {
    height: 5rem;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.sign_out {
    all: unset;

    width: 80%;
    height: 3rem;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: .5rem;

    background: rgba(255, 255, 255, 0.1);
    border-radius: 12px;

    cursor: pointer;
}

.sign_out_icon {
    width: 1.5rem;
    height: 1.5rem;
}

.sign_out_text {
    font-family: 'Lato', sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 24px;

    color: #FFFFFF;
}
</style>