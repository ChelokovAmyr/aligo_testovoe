<script setup lang="ts">

</script>

<template>
  <footer class="footer">
    <div class="footer__inner">
    <div class="footer__left">
      <span class="footer__left__text">Пользовательское соглашение</span>
    </div>
    <div class="footer__right">
      <div class="footer__right__dots">
        <div class="footer__right__dot" v-for="(dot, index) in 3" :key="index"></div>
      </div>
      <div class="footer__contacts">
        <span class="footer__contacts__number"><strong>8 (800) 000-00-00</strong></span>
        <span class="footer__contacts__time">пн-пт с 10:00 до 19:00</span>
      </div>
    </div>
    </div>
  </footer>
</template>

<style scoped lang="scss">
  .footer{
    margin-top: 42px;
    background: #D9D9D9;
    height: 102px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .footer__left__text{
    font-size: 14px;
    text-decoration: underline;
  }
  .footer__inner{
    margin: 0 auto;
    width: 100%;
    max-width: 1120px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .footer__right__dot{
    width: 18px;
    height: 18px;
    border-radius: 50px;
    display: inline-block;
    margin: 0 12px;
    background: #FFFFFF;
  }
  .footer__right {
    display: flex;
    align-items: center;
  }
  .footer__contacts{
    margin-left: 80px;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }
  .footer__contacts__number{
    font-size: 14px;
    margin-bottom: 12px;
  }
  .footer__contacts__time{
    font-size: 14px;
  }
</style>
