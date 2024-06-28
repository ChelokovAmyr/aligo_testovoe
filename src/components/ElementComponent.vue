<script setup lang="ts">

</script>

<template>
  <div class="element__item">
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
