<template>
  <div>
    <label class="form-label" id="child-id">
      {{ label }}
    </label>
    <input type="text" v-model="value" class="form-control" />
  </div>
</template>

<script>
import { computed } from "vue";

export default {
  props: ["modelValue", "label"],
  emits: ["update:modelValue"],
  setup(props, context) {
    const value = computed({
      get() {
        return props.modelValue;
      },
      set(value) {
        context.emit("update:modelValue", value);
      },
    });

    return { value };
  },
};
</script>

<style lang="scss" scoped></style>
