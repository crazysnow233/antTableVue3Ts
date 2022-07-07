<template>
  <div class="about">
    <h1>This is an about page</h1>
    <a-button>你好</a-button>
  </div>
</template>
<script lang="ts" setup>
import { Modal } from "ant-design-vue";
Modal.error({
  content: "你哈",
});
</script>
