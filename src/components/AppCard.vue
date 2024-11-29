<template>
  <div class="card">
    <div v-if="$slots.header" class="card-header">
      <slot name="header" header-message="헤더 메시지">#Header</slot>
    </div>
    <div v-if="$slots.default" class="card-body">
      <slot :child-message="childMessage" hello-message="안녕">#Body</slot>
      <!-- <h5 class="card-title">Special title treatment</h5>
      <p class="card-text">
        With supporting text below as a natural lead-in to additional content.
      </p>
      <a href="#" class="btn btn-primary">Go somewhere</a> -->
    </div>
    <div v-if="$slots.footer" class="card-footer text-muted">
      <slot name="footer" footer-message="푸터 메시지">#Footer</slot>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup(_, { slots }) {
    const childMessage = ref("child message");
    return { childMessage };
  },
};
</script>

<style lang="scss" scoped></style>
