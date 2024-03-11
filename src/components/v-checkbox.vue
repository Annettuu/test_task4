<template>
    <input
        class="v-checkbox"
        type="checkbox"
        :checked="props.modelValue"
        @input="emit('update:modelValue', props.modelValue)"
    />
</template>

<script setup>
const props = defineProps(['modelValue'])
const emit = defineEmits(['update:modelValue'])
</script>

<style scoped>
.v-checkbox[type=checkbox] {
  position: relative;
  cursor: pointer;
  line-height: 0;
  border: 1px solid #000;
  background: white;
  margin: 0;
  outline: 0;
  padding: 0;
  vertical-align: sub;
  height: 20px;
  width: 20px;
  -webkit-appearance: none;
}
.v-checkbox[type=checkbox]:checked:before {
  opacity: 1;
}
.v-checkbox[type=checkbox]:before {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: block;
  content: '';
  width: 20px;
  height: 20px;
  background: black;
  z-index: 2;
  opacity: 0;
}
</style>