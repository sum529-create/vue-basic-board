<template>
  <div>
    {{ $parent }}
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const message = ref("hi!");
    const sayHi = () => {
      alert(message.value);
    };

    return { message, sayHi };
  },
};
</script>

<style lang="scss" scoped></style>
