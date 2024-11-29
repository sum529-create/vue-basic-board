<template>
  <div class="container py-4">
    <div class="card">
      <div class="card-header">ProviderInject</div>
      <div class="card-body">
        <button @click="count++">Button</button>
        <p>{{ appMessage }}</p>
        <child />
      </div>
    </div>
  </div>
</template>

<script>
import { inject, provide, ref } from "vue";
import Child from "./Child.vue";
export default {
  components: { Child },
  setup() {
    const staticMessage = "static Message";
    const message = ref("message");
    // 만약 자식에서 provide값을 변경하지 말고 변경해야할 일이 있을 경우,
    // 부모에서 변경할 값을 함께 보내야함
    const count = ref(10);
    const updateMessage = (data) => {
      message.value += data;
    };
    // provide("static-message", staticMessage);
    // {}객체형태로 함께 보낼것
    provide("message", { message, updateMessage });
    provide("count", count);

    const appMessage = inject("app-message");

    return { count, appMessage };
  },
};
</script>

<style lang="scss" scoped></style>
