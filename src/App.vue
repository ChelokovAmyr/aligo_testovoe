<template>
  <router-view/>
  <FooterComponent/>
</template>

<style lang="scss">
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: sans-serif;
  }

</style>
<script setup lang="ts">
import FooterComponent from "@/components/FooterComponent.vue";
</script>
