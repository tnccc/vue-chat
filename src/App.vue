<script setup lang="ts">
import GlobalHeader from './components/GlobalHeader.vue';
</script>

<template>
  <GlobalHeader 
    :class="$style.header"
    :loginStatus="true"
  />
  <main>
  </main>
</template>

<style lang="scss" module>
.header {
  color: var(--white);
}
</style>
