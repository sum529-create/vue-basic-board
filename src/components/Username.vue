<template>
  <div>
    <label-input
      :modelValue="firstname"
      @update:modelValue="$emit('update:firstname', $event)"
      label="성"
    />
    <label-input
      :modelValue="lastname"
      @update:modelValue="$emit('update:lastname', $event)"
      label="이름"
    />
  </div>
</template>

<script>
import LabelInput from "./LabelInput.vue";
export default {
  components: { LabelInput },
  props: ["firstname", "lastname"],
  emits: ["update:firstname", "update:lastname"],
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped></style>
