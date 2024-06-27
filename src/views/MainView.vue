<template>
  <main class="main">
    <HeaderComponent/>
    <MainComponent/>
  </main>
</template>

<script lang="ts" setup>

import HeaderComponent from "@/components/HeaderComponent.vue";
import MainComponent from "@/components/MainComponent.vue";
</script>

<style lang="scss" scoped>
  .main{
    margin: 0 auto;
    max-width: 1120px;
  }
</style>
