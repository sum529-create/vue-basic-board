<template>
  <div class="container py-4">
    <div class="btn btn-primary me-2" @click="changeCurrentComp(DynamicApple)">
      사과
    </div>
    <div class="btn btn-danger" @click="changeCurrentComp(DynamicBanana)">
      바나나
    </div>
    <hr />
  </div>
  <!-- <dynamic-apple />
  <dynamic-banana /> -->
  <component :is="currentComp" />

  <p>{{ obj1 }}</p>
  <p>{{ obj2 }}</p>
</template>

<script setup>
import { ref, shallowRef } from "vue";
import DynamicApple from "./DynamicApple.vue";
import DynamicBanana from "./DynamicBanana.vue";

const currentComp = shallowRef(DynamicApple);
// 속성 값 자체 변경시 : ref(반응), shallowRef(무반응) string -> string
// 데이터 형식 값 변경 시 : ref(반응), shallowRef(반응) object -> string
const obj1 = ref({ name: "rudy" });
const obj2 = shallowRef({ name: "kelly" });
const changeCurrentComp = (comp) => (currentComp.value = comp);
</script>

<style lang="scss" scoped></style>
