<script setup lang="ts">
import VPagination from "@hennge/vue3-pagination";
import "@hennge/vue3-pagination/dist/vue3-pagination.css";

import {ref, computed} from 'vue';
import ElementComponent from "@/components/ElementComponent.vue";
  const inputNumber = ref('');

  const pageSize = ref(10);

  const currentPage = ref(1)

  const indexStart = computed(()=> {
    return (currentPage.value - 1) * pageSize.value;
  })

  const indexEnd = computed(()=> {
    return indexStart.value + pageSize.value;
  })
  const paginatedArray = computed(()=> {
    return cardsArray.value.slice(indexStart.value, indexEnd.value);
  })

  const cardsArray = ref([
    {serialNumber: 'А555АА', cityNumber: '61', dateNumber: '16.07.2024', cityTitle: 'г. Ростов-на-Дону',priceNumber: '300000', rating: 1 },
    {serialNumber: 'C799RE', cityNumber: '86', dateNumber: '04.07.2024', cityTitle: 'г. Москва',priceNumber: '527221', rating: 8 },
    {serialNumber: 'E555ED', cityNumber: '87', dateNumber: '16.07.2024', cityTitle: 'г. Верхоянск',priceNumber: '853907', rating: 4 },
    {serialNumber: 'А817АS', cityNumber: '49', dateNumber: '07.10.2024', cityTitle: 'г. Санкт-Петербург',priceNumber: '530411', rating: 10 },
    {serialNumber: 'B841PF', cityNumber: '97', dateNumber: '28.11.2024', cityTitle: 'г. Владивосток',priceNumber: '130789', rating: 2 },
    {serialNumber: 'G230OА', cityNumber: '99', dateNumber: '23.10.2024', cityTitle: 'г. Сызрань',priceNumber: '627764', rating: 6 },
    {serialNumber: 'L929BА', cityNumber: '94', dateNumber: '16.10.2024', cityTitle: 'г. Кызыл',priceNumber: '736318', rating: 7 },
    {serialNumber: 'L929BА', cityNumber: '93', dateNumber: '14.10.2024', cityTitle: 'г. Верхние Луки',priceNumber: '805267', rating: 5 },
    {serialNumber: 'L929BА', cityNumber: '78', dateNumber: '24.12.2024', cityTitle: 'г. Севастополь',priceNumber: '544087', rating: 8 },
    {serialNumber: 'L929BА', cityNumber: '52', dateNumber: '11.10.2024', cityTitle: 'г. Нижнекамск',priceNumber: '914610', rating: 5 },
    {serialNumber: 'L929BА', cityNumber: '45', dateNumber: '27.12.2024', cityTitle: 'г. Ростов-на-Дону',priceNumber: '770881', rating: 7 },
    {serialNumber: 'L929BА', cityNumber: '93', dateNumber: '05.09.2024', cityTitle: 'г. Ростов-на-Дону',priceNumber: '406419', rating: 8 },
    {serialNumber: 'L929BА', cityNumber: '11', dateNumber: '01.10.2024', cityTitle: 'г. Ростов-на-Дону',priceNumber: '553058', rating: 9 },
    {serialNumber: 'L929BА', cityNumber: '97', dateNumber: '11.10.2024', cityTitle: 'г. Ростов-на-Дону',priceNumber: '829569', rating: 7 },
    {serialNumber: 'L929BА', cityNumber: '53', dateNumber: '09.10.2024', cityTitle: 'г. Ростов-на-Дону',priceNumber: '343494', rating: 10 },
    {serialNumber: 'L929BА', cityNumber: '70', dateNumber: '23.09.2024', cityTitle: 'г. Ростов-на-Дону',priceNumber: '381580', rating: 1 },
    {serialNumber: 'L929BА', cityNumber: '55', dateNumber: '25.07.2024', cityTitle: 'г. Ростов-на-Дону',priceNumber: '202566', rating: 6 },
    {serialNumber: 'L929BА', cityNumber: '38', dateNumber: '16.08.2024', cityTitle: 'г. Ростов-на-Дону',priceNumber: '459990', rating: 10 },
    {serialNumber: 'L929BА', cityNumber: '92', dateNumber: '08.07.2024', cityTitle: 'г. Ростов-на-Дону',priceNumber: '297686', rating: 2 },
    {serialNumber: 'L929BА', cityNumber: '65', dateNumber: '05.11.2024', cityTitle: 'г. Ростов-на-Дону',priceNumber: '126762', rating: 9 },
  ]);

  const popularCard = computed(()=> {
    return JSON.parse(JSON.stringify(cardsArray.value)) .slice(0,8).sort((a, b) => b.rating - a.rating)
  })
  const updateHandler = (page:number) => {
    console.log(page)
  }

  const selectCardsByDateValue = ref('new')

  const selectCardsByDate = (option:string) => {
    if (option === 'new') {
      paginatedArray.value.sort(function(a, b){
        let aa = a.dateNumber.split('.').reverse().join(),
            bb = b.dateNumber.split('.').reverse().join();
        return aa < bb ? -1 : (aa > bb ? 1 : 0);
      });
    }
    if (option === 'old') {
      paginatedArray.value.sort(function(a, b){
        let aa = a.dateNumber.split('.').reverse().join(),
            bb = b.dateNumber.split('.').reverse().join();
        return bb < aa ? -1 : (bb > aa ? 1 : 0);
      });
    }
  }
</script>

<template>
  <div class="main-wrapper">
    <h1>Продажа автомобилей с красивыми номерами</h1>
    <div class="main-section">
        <div class="main-section__left main-section__item">
          <div class="input-number-section">
            <span class="main-section__left__heading">Поиск номеров</span>
            <div class="input__number__wrap">
              <input type="text" class="input__number" v-model="inputNumber" maxlength="6" minlength="6" placeholder="******">
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
    <select class="select__main" v-model="selectCardsByDateValue" @change="selectCardsByDate(selectCardsByDateValue)">
      <option class="option__main" value="new">
        Сначала свежие
      </option>
      <option class="option__main" value="old">
        Сначала старые
      </option>
    </select>
    </div>
    <div class="elements-section">
      <ElementComponent  v-for="(item,index) in paginatedArray" :key="index" :item="item"/>
    </div>
    <div class="pagination-section">
      <v-pagination
          v-model="currentPage"
          :pages="Math.round(cardsArray.length / 10)"
          hideFirstButton
          hideLastButton
          active-color="#DCEDFF"
          @update:modelValue="updateHandler"
      />
    </div>
    <h2 class="popular-section__heading">Популярные объявления</h2>
    <div class="elements-section">
      <ElementComponent  v-for="(item,index) in popularCard" :key="index" :item="item"/>
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
    &::placeholder{
      position: absolute;
      left: 0;
      right: 0;
      font-size: 40px;
      color: black;
    }
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
    font-size: 60px;
    height: 45px;
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

