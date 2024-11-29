<template>
  <div class="card">
    <div class="card-body">
      <span class="badge text-bg-secondary">{{isContentType}}</span>
      <h5 class="card-title red mt-2">{{title}}</h5>
      <p class="card-text">
        {{content}}
      </p>
      <a href="#" class="btn" :class="isLikeClass">좋아요</a>
    </div>
  </div>
</template>

<script>
import { computed, ref, useCssModule } from 'vue';

export default {
  props:{
    type:{
      type: String,
      default: 'news',
      validator: value => {
        return ['news', 'notice'].includes(value)
      }
    },
    title:{
      type: String,
      required: true,
    },
    content: {
      type: String,
      // required: true,
    },
    isLike:{
      type: Boolean,
      default: false,
    }
  },
  setup (props) {
    // const style = useCssModule();
    // console.log('style: ', style);
    const color = ref('red');
    color.value = 'blue';

    const isLikeClass = computed(() => props.isLike ? 'btn-danger' : 'btn-outline-danger')

    const isContentType = computed(() => props.type === 'news' ? '뉴스' : '공지사항');

    return {color, isLikeClass, isContentType}
  }
}
</script>

<style lang="scss" module>
.red{
  color: v-bind(color) !important;
}
</style>