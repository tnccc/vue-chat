<script setup lang="ts">
import GlobalHeader from './components/GlobalHeader.vue';
import LoginForm from './components/LoginForm.vue';

</script>

<template>
  <GlobalHeader 
    :class="$style.header"
    :loginStatus="true"
  />
  <main
    :class="$style.main"
  >
    <LoginForm></LoginForm>
  </main>
</template>

<style lang="scss" module>
.header {
  width           : 100%;
  background-color: var(--black);
}
</style>
