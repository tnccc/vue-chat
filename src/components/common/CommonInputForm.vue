<script setup lang="ts">
import { toRefs } from 'vue';
import { IconEyeClosed } from '@tabler/icons-vue';

type Props = {
  heading?: string,
  type?: string,
  shouldPassword?: boolean,
  placeholder?: string,
  required?: boolean,
}

type Emits = {
  (e: string, val: any): void
}

const props = withDefaults(defineProps<Props>(), {
  heading       : '',
  type          : '',
  placeholder   : '',
  shouldPassword: false,
  required      : false,
})

const isShowPassword = () => {
  const { shouldPassword } = toRefs(props)
  shouldPassword.value = !shouldPassword.value
}

</script>

<template>
  <div
    :class="$style.container"
  >
    <label 
      :class="$style.heading"
      :required="required"
    >
      {{ heading }}
      {{ isShowPassword }}
    </label>
    <input 
      :class="[$style.input, $style[type]]"
      :required="required"
      :placeholder="placeholder"
      :type="type"
    >
    <span
      v-if="type === 'password'"
      :class="$style.icon"
      @click="isShowPassword"
    >
      <IconEyeClosed />
    </span>
  </div>
</template>

<style lang="scss" module>
.container {
  position             : relative;
  width                : 100%;
  color                : var(--black);
  --password-icon-width: calc(var(--bv) * 2.5);

  &:not(:first-of-type) {
    margin-top: calc(var(--bv) * 1.5);
  }

  .heading {
    font-size: var(--font-size-small);
  }

  .input {
    margin-top: calc(var(--bv) * 1.5);
    padding      : 5px var(--bv) var(--bv);
    width        : 100%;
    max-height   : calc(var(--bv) * 5);
    color        : var(--black);
    border       : solid 1px var(--black);
    border-radius: 5px;

    &::placeholder {
      font-size: calc(var(--bv) * 1.5);
    }

    &.password {
      position: relative;
      padding: 5px calc(var(--bv) + var(--password-icon-width) + 10px) var(--bv) var(--bv);
    }
  }
  .icon {
      position: absolute;
      top     : calc(var(--bv) * 5.85);
      right   : calc(var(--bv) * 1.5);
      display : inline-block;
      width   : var(--password-icon-width);
      cursor  : pointer;
      
      svg {
        width: 100%;
      }
    }
}
</style>