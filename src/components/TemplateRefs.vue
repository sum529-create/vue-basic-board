<template>
  <div class="conainer py-4">
    <input type="text" ref="input" />
    <p v-if="input">
      {{ input.value }}
      <br />
      {{ $refs.input.value }}
    </p>
    <hr />
    <ul>
      <!-- <li v-for="fruit in fruits" :key="fruit" ref="itemRefs"> -->
      <li v-for="fruit in fruits" :key="fruit" :ref="(el) => itemRefs.push(el)">
        {{ fruit }}
      </li>
    </ul>
    <TemplateRefsChild ref="child" />
  </div>
</template>

<script>
import { onMounted, ref } from "vue";
import TemplateRefsChild from "./TemplateRefsChild.vue";

export default {
  components: { TemplateRefsChild },
  setup() {
    const input = ref(null);
    const fruits = ref(["사과", "딸기", "포도"]);
    const itemRefs = ref([]);
    const child = ref(null);

    // result: null : created단계이기에 DOM미조회
    console.log("setup: ", input.value);

    onMounted(() => {
      input.value.value = "hello world";

      // result: <input type="text"/> : 렌더링 된 이후이기에 화면에 DOM조회
      console.log("onMounted: ", input.value);

      // itemRefs에 하나씩 item이 담겨 dom형태로 출력하게 된다.
      itemRefs.value.forEach((item) => console.log("item :", item));

      // 자식 컴포넌트에서 ref접근
      child.value.sayHi();
    });
    return { input, fruits, itemRefs, child };
  },
};
</script>

<style lang="scss" scoped></style>
