<script setup lang="ts">
import {ref} from 'vue';

const menuItems = ref([
    'Каталог номеров',
    'Оформление',
    'Разместить объявление',
    'Продать быстро'
])
</script>

<template>
  <header class="header">
    <div class="header-contacts">
      <div class="header__points-block">
        <div class="header__circle" v-for="(circle, index) in 3" :key="index">
        </div>
      </div>
      <div class="header__contact-details">
        <span class="header__work-time">пн-пт&nbsp;с&nbsp;10:00&nbsp;до&nbsp;19:00</span>
        <span class="header__work-number"><strong>8&nbsp;(800)&nbsp;000-00-00</strong></span>
        <button class="header__call-me-btn">Перезвоните&nbsp;мне</button>
      </div>
    </div>
    <div class="header-menu">
      <img src="@/assets/Лого.png" alt="">
      <ul class="header-menu-ul">
        <li v-for="menuItem in menuItems" :key="menuItem">
          {{menuItem}}
        </li>
      </ul>
      <button class="header-menu__button">Вход</button>
    </div>
  </header>
</template>

<style scoped lang="scss">
  .header{
    display: flex;
    flex-direction: column;
    &-menu{
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding-bottom: 12px;
      border-bottom: 1px solid black;
    }
    &-contacts{
      display: flex;
      justify-content: space-between;
      margin: 9px 0;
      padding: 4px 0;
      border-bottom: 1px solid black;
      font-family: 'Montserrat', sans-serif;
    }
    &__circle{
      display: inline-block;
      width: 18px;
      height: 18px;
      border-radius: 40px;
      background: #D9D9D9;
      margin-right:   23px;
    }
    &__work-time{
      font-size: 14px;
      display: inline-block;
      margin-right: 34px;
    }
    &__work-number{
      display: inline-block;
      margin-right: 34px;
    }
    &__call-me-btn{
      text-transform: uppercase;
      padding: 5px 14px;
      border-radius: 8px;
      background: #D9D9D9;
      outline: none;
      border: none;
    }
  }
  .header-menu-ul{
    display: flex;
    align-items: center;
    list-style-type: none;
    font-family: 'Montserrat', sans-serif;
    li{
      font-size: 14px;
      margin: 0 19px;
      text-transform: uppercase;
    }
  }
  .header-menu__button{
    display: inline-block;
    background: #D9D9D9;
    padding: 15px 29px;
    text-transform: uppercase;
    outline: none;
    border: none;
    border-radius: 8px;
  }
</style>
