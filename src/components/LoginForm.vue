<script setup lang="ts">
import CommonInputForm from './common/CommonInputForm.vue';

</script>

<template>
  <div
    :class="$style.container"
  >
    <form>
      <CommonInputForm
        :heading="'メールアドレス'"
        :type="'email'"
        :placeholder="'メールアドレス'"
        :required="true"
      />
      <CommonInputForm
        :heading="'パスワード'"
        :type="'password'"
        :placeholder="'パスワード'"
        :required="true"
      />
    </form>
  </div>
</template>

<style lang="scss" module>
.container {
  margin: 0 auto;
  width : 320px;
}

</style>