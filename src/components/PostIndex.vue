<template>
  <main class="container py-4">
    <post-create @createPost="createPost" />
    <hr class="my-4" />
    <div class="row g-3">
      <div v-for="(item, i) in posts" class="col col-4" :key="i">
        <post-item
          :title="item.title"
          :content="item.content"
          :type="item.type"
          :is-like="item.isLike"
        />
      </div>
    </div>
    <hr class="my-4" />
    <label-input v-model="username" label="이름" />
    <!-- <label-title v-model:title="username" label="제목"/>
    <username v-model:firstname="firstname" v-model:lastname="lastname"/> -->
  </main>
</template>

<script>
import { reactive, ref } from "vue";
import PostItem from "./PostItem.vue";
import PostCreate from "./PostCreate.vue";
import LabelInput from "./LabelInput.vue";
import LabelTitle from "./LabelTitle.vue";
import Username from "./Username.vue";
export default {
  components: { PostItem, PostCreate, LabelInput, LabelTitle, Username },
  setup() {
    const posts = reactive([
      { type: "news", title: "title01", content: "content01", isLike: true },
      { type: "notice", title: "title02", content: "content02" },
      { type: "news", title: "title03", content: "content03" },
    ]);

    const createPost = (newPost) => {
      posts.push(newPost);
    };
    const username = ref("");
    const firstname = ref("");
    const lastname = ref("");
    return { posts, createPost, username, firstname, lastname };
  },
};
</script>

<style lang="scss" scoped></style>
