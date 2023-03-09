<script setup lang="ts">
import CommonInputForm from './common/CommonInputForm.vue';
import CommonButton from './common/CommonButton.vue';

const test = () => console.log('発火')

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
      <div
        :class="$style.operate"
      >
        <NuxtLink
          :class="$style.link"
        >
          新規作成はコチラから
        </NuxtLink>
        <CommonButton
          @onClick="test"
          :class="$style.button"
          :text="'ログイン'"
        />
      </div>
    </form>
  </div>
</template>

<style lang="scss" module>
@use '@/assets/scss/mixin' as m;

.container {
  margin: 0 auto;
  width : 320px;

  .operate {
    margin-top     : calc(var(--bv) * 2);
    display        : flex;
    align-items    : center;
    justify-content: space-between;

    .button {
      width: 55%;

      &:hover {
        color           : var(--blue);
        background-color: var(--white);
        border          : solid 1px var(--blue);
      }
    }

    .link {
      font-size: var(--font-size--smallest);
    }
  }
}

</style>