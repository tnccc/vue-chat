<script setup lang="ts">

type Props = {
  text: string,
}

type Emits = {
  (e: string): void
}

const props = withDefaults(defineProps<Props>(), {
  text: '',
})

const emit = defineEmits<Emits>()
const onClick = (): void => {
  emit('onClick')
}
</script>

<template>
  <button
    @click="onClick"
    :class="$style.button"
  >
    {{ text }}
  </button>
</template>

<style lang="scss" module>
@use '@/assets/scss/mixin' as m;

.button {
  @include m.commonButton(100%, 100%, 5px, #FFFFFF, #2271b1, #2271b1);
  padding: var(--bv);
  transition: background-color .3s, color .3s;
}
</style>