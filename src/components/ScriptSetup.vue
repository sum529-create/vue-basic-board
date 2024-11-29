<template>
  <div class="container py-4">
    <post-item type="news" title="제목" contens="내용" :is-like="true" />
    <hr />
    <template-refs-child ref="child" />
    <template v-if="child">{{ child.message }}</template>
    <hr />
    <my-button class="parent-class">Button</my-button>
  </div>
</template>

<script setup>
import postItem from "@/components/setup/PostItem.vue";
import TemplateRefsChild from "@/components/setup/TemplateRefsChild.vue";
import MyButton from "@/components/setup/MyButton.vue";
import { ref } from "vue";
import axios from "axios";

const child = ref(null);
const msg = "hihi";
defineExpose({
  msg,
});

const response = await axios("https://jsonplaceholder.typicode.com/posts");
console.log(response);
</script>

<style lang="scss" scoped></style>
