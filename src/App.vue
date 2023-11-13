<script setup>
import { NConfigProvider, NMessageProvider } from 'naive-ui'
import Home from './page/Home.vue'
console.log('👋 This message is being logged by "App.vue", included via Vite');
</script>

<template>
  <!-- configuring the global font weight -->
  <n-config-provider :theme-overrides="{ common: { fontWeightStrong: '600' } }">
    <n-message-provider>
      <Home />
    </n-message-provider>
  </n-config-provider>
</template>