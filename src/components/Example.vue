<template>
  <main>
    <div class="container py-4">
      <my-button class="btn btn-line" id="parent-button" @click="onAlert()" />
      <label-input label="이름" data-id="id" />
      <hr />
      <fancy-button v-slot="{ fancyMessage }">{{ fancyMessage }}</fancy-button>
      <hr />
      <app-card>
        <template v-slot:header="{ headerMesaage }">
          {{ headerMesaage }}
        </template>
        <template v-slot:default="{ childMessage, helloMessage }">
          <br />
          {{ childMessage }}
          <br />
          {{ helloMessage }}
        </template>
        <!-- 암시적인 default 슬롯 -->
        <template #footer="{ footerMessage }"> {{ footerMessage }} </template>
      </app-card>
    </div>
  </main>
</template>

<script>
import AppCard from "./AppCard.vue";
import FancyButton from "./FancyButton.vue";
import LabelInput from "./LabelInput.vue";
import MyButton from "./MyButton.vue";
export default {
  components: { MyButton, LabelInput, FancyButton, AppCard },
  setup() {
    function onAlert() {
      return alert("알럿창을 띄움");
    }
    return { onAlert };
  },
};
</script>

<style lang="scss" scoped></style>
