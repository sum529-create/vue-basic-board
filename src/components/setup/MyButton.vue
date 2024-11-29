<template>
  <div class="p-3 bg-danger">
    <button class="btn btn-primary" type="button" v-bind="$attrs">
      My Button
    </button>
  </div>
</template>

<script>
export default {
  inheritAttrs: false,
  setup(_, { attrs }) {
    // console.log("context attrs: ", attrs);
    // console.log("class: ", attrs.class);
    // console.log("id: ", attrs.id);
    // console.log("onClick: ", attrs.onClick);

    return {};
  },
};
</script>

<style lang="scss" scoped></style>
