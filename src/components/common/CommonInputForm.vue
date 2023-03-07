<script setup lang="ts">

interface Props {
  heading?: string,
  type?: string,
  placeholder?: string,
  required?: boolean,
}

const props = withDefaults(defineProps<Props>(), {
  heading    : '',
  type       : '',
  placeholder: '',
  required   : false,
})
</script>

<template>
  <p
    :class="$style.container"
  >
    <label 
      :class="$style.heading"
      :required="required"
    >
      {{ heading }}
    </label>
    <input 
      :class="$style.input"
      :required="required"
      :placeholder="placeholder"
      :type="type"
    >
  </p>
</template>

<style lang="scss" module>
.container {
  width: 100%;
  color: var(--black);

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
  }
}
</style>