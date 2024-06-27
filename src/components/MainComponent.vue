<script setup lang="ts">
import VPagination from "@hennge/vue3-pagination";
import "@hennge/vue3-pagination/dist/vue3-pagination.css";

import {ref} from 'vue';
  const inputNumber = ref('');

  const numbersArray = ref([]);
</script>

<template>
  <div class="main-wrapper">
    <h1>Продажа автомобилей с красивыми номерами</h1>
    <div class="main-section">
        <div class="main-section__left main-section__item">
          <div class="input-number-section">
            <span class="main-section__left__heading">Поиск номеров</span>
            <div class="input__number__wrap">
              <input type="text" class="input__number" v-model="inputNumber" maxlength="6" minlength="6">
              <div class="input-number__tail">
                <span class="input-number__tail__star">*</span>
                <div class="flag-section">
                  <div class="flag-section__flag"></div>
                  <span class="flag-section__title">RUS</span>
                </div>
              </div>
            </div>
          </div>
          <div class="checkbox__wrap">
            <label class="checkbox__wrap__item">
              <input type="checkbox" name="agree"><span>Одинаковые буквы</span>
            </label>
            <label class="checkbox__wrap__item">
              <input type="checkbox" name="agree"><span>Первая десятка</span>
            </label>
            <label class="checkbox__wrap__item">
              <input type="checkbox" name="agree"><span>Одинаковые цифры</span>
            </label>
            <label class="checkbox__wrap__item">
              <input type="checkbox" name="agree"><span>Зеркальные цифры</span>
            </label>
          </div>
        </div>
        <div class="main-section__right  main-section__item">
          <div class="picture-section">
            <img src="@/assets/Star%205.png" class="picture-section__item" alt="">
            <img src="@/assets/Star%206.png" class="picture-section__item" alt="">
          </div>
          <p class="picture-section__text">Сделки с госномерами осуществляются в соответствии с законами Российской Федарации и проводятся путем продажи автомобиля новому владельцу вместе с номером.</p>
        </div>
    </div>
    <div class="select-wrap">
    <select class="select__main">
      <option class="option__main">
        Сначала свежие
      </option>
      <option>
        Сначала старые
      </option>
    </select>
    </div>
    <div class="elements-section">
      <div class="element__item" v-for="(item,index) in 12" :key="index">
        <p class="element__item__date">25.09.23</p>
        <div class="element__item__inner">
          <div class="element__item__number">
            <strong><span class="element__item__number__small">А</span>555<span class="element__item__number__small">АА</span></strong>
          </div>
          <div class="element__item__flag">
            <span class="element__item__flag__region"><strong>61</strong></span>
            <div class="element__item__flag__inner">
              <div class="element__item__flag__inner__element"></div>
              <span class="element__item__flag__inner__title"><strong>RUS</strong></span>
            </div>
          </div>
        </div>
        <div class="element__item__bottom">
          <span class="element__item__bottom__city">г. Ростов-на-Дону</span>
          <span class="element__item__bottom__price">300 000р</span>
        </div>
      </div>
    </div>
    <div class="pagination-section">
      <v-pagination
          v-model="page"
          :pages="10"
          :range-size="1"
          active-color="#DCEDFF"
          @update:modelValue="updateHandler"
      />
    </div>
    <h2 class="popular-section__heading">Популярные объявления</h2>
    <div class="elements-section">
      <div class="element__item" v-for="(item,index) in 8" :key="index">
        <p class="element__item__date">25.09.23</p>
        <div class="element__item__inner">
          <div class="element__item__number">
            <strong><span class="element__item__number__small">А</span>555<span class="element__item__number__small">АА</span></strong>
          </div>
          <div class="element__item__flag">
            <span class="element__item__flag__region"><strong>61</strong></span>
            <div class="element__item__flag__inner">
              <div class="element__item__flag__inner__element"></div>
              <span class="element__item__flag__inner__title"><strong>RUS</strong></span>
            </div>
          </div>
        </div>
        <div class="element__item__bottom">
          <span class="element__item__bottom__city">г. Ростов-на-Дону</span>
          <span class="element__item__bottom__price">300 000р</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
  h1{
    font-weight: 400;
    font-family: sans-serif;
    text-align: center;
    font-size: 36px;
    margin: 11px auto 25px auto;
    display: block;
  }
  .main-section{
    border-radius: 16px;
    padding: 22px 99px;
    border: 1px solid black;
    display: flex;
    justify-content: space-between;
  }
  .main-section__item{
   width: 50%;
  }
  .checkbox__wrap{
    display: grid;
    grid-template-columns: auto auto;
  }
  .main-section__right{
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
  }
  .picture-section{
    margin-bottom: 23px;
  }
  .picture-section__text{
    font-size: 12px;
  }
  .main-section__left__heading{
    font-size: 24px ;
    margin-bottom: 14px;
  }
  .input-number-section{
    display: flex;
    justify-content: flex-start;
    flex-direction: column;
    margin-bottom: 27px;
  }
  .checkbox__wrap__item{
    display: flex;
    align-items: center;
    margin-bottom: 22px;
    span{
      margin-left: 3px;
    }
    input{
      width: 20px;
      height: 20px;
      background-color: #D9D9D9;
    }
    label{
      margin-left: 3px;
    }
  }
  .input__number__wrap {
    display: flex;
    align-items: center;
    border: 4px solid black;
    width: 300px;
    border-radius: 10px;
  }
  .input__number {
    border: none;
    outline: none;
    width: 70%;
    padding: 11px;
    font-size: 20px;
    text-align: center;
  }
  .input-number__tail{
    padding: 11px;
    border-left: 4px solid black;
    height: 100%;
    width: 30%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .input-number__tail__star{
    font-size: 20px;
  }
  .select-wrap {
    display: flex;
    justify-content: flex-end;
    margin-top: 23px;
  }
  .elements-section{
    display: grid;
    grid-template-columns: auto auto auto auto;
  }
  .element__item {
    border: 1px solid black;
    margin: 10px;
    padding: 10px 27px;
    border-radius: 16px;
    &:nth-child(4n + 1){
      margin-left: 0;
    }
    &:nth-child(4n + 4){
      margin-right: 0;
    }
  }
  .element__item__date{
    font-size: 10px;
    margin-bottom: 3px;
  }
  .element__item__flag__inner__title{
    font-size: 15px;
    margin-left: 2px;
  }
  .element__item__flag__region{
    font-size: 30px;
  }
  .element__item__inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    border: 3px solid black;
    margin-bottom: 3px;
    border-radius: 10px;
  }
  .element__item__number {
    font-size: 30px;
    text-align: center;
    width: 100%;
  }
  .element__item__number__small{
    font-size: 20px;
  }
  .element__item__bottom__city {
    font-size: 12px;
  }
  .element__item__bottom {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .element__item__bottom__price{
    font-size: 12px;
  }
  .element__item__flag__inner__element {
    width: 18px;
    height: 9px;
    background: #D9D9D9;
  }
  .element__item__flag__inner {
    display: flex;
    align-items: center;
  }
  .element__item__flag {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border-left: 3px solid black;
    padding: 11px 8px 11px 4px;
  }
  .select__main{
    border-radius: 8px;
    padding: 7px 16px;
    text-align: center;
    outline: none;
    cursor: pointer;
  }
  .option__main{
    cursor: pointer;
    text-align: center;
  }
  .main-wrapper{
    padding-bottom: 100px;
  }
  .popular-section__heading{
    font-size: 36px;
    margin-bottom: 24px;
    text-align: center;
    font-weight: 400;
    margin-top: 46px;
  }
  .pagination-section{
    margin-top: 46px;
    border-radius: 16px;
    border: 1px solid black;
    padding: 17px 28px;
  }
</style>

