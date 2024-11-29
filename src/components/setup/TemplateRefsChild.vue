<template>
  <div>
    {{ $parent }}
  </div>
</template>

<script setup>
import { ref } from "vue";

const message = ref("hi!");
const sayHi = () => {
  alert(message.value);
};

defineExpose({
  message,
  sayHi,
});
</script>

<style lang="scss" scoped></style>
