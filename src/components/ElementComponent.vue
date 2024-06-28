<script setup lang="ts">
import {defineProps} from 'vue'
const props = defineProps(['item'])
</script>

<template>
  <div class="element__item">
    <p class="element__item__date">{{item.dateNumber}}</p>
    <div class="element__item__inner">
      <div class="element__item__number">
        <strong><span class="element__item__number__small">{{item.serialNumber.slice(0,1)}}</span>{{item.serialNumber.slice(1,4)}}<span class="element__item__number__small">{{item.serialNumber.slice(4,6)}}</span></strong>
      </div>
      <div class="element__item__flag">
        <span class="element__item__flag__region"><strong>{{item.cityNumber}}</strong></span>
        <div class="element__item__flag__inner">
          <div class="element__item__flag__inner__element"></div>
          <span class="element__item__flag__inner__title"><strong>RUS</strong></span>
        </div>
      </div>
    </div>
    <div class="element__item__bottom">
      <span class="element__item__bottom__city">{{item.cityTitle}}</span>
      <span class="element__item__bottom__price">{{item.priceNumber.slice(0,3)}} {{item.priceNumber.slice(3,6)}} р</span>
    </div>
  </div>
</template>

<style scoped lang="scss">
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
</style>
