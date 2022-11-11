<template>
  <section>
    <a-tree
      v-model:expandedKeys="expandedKeys"
      v-model:selectedKeys="selectedKeys"
      v-model:checkedKeys="checkedKeys"
      :load-data="onLoadData"
      :tree-data="treeData"
      checkable
      @check="handleCheck"
    />
  </section>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import type { TreeProps } from "ant-design-vue";
const expandedKeys = ref<string[]>([]);
const selectedKeys = ref<string[]>([]);
const treeData = ref<TreeProps["treeData"]>([
  { title: "Expand to load", key: "0" },
  { title: "Expand to load", key: "1" },
  { title: "Tree Node", key: "2", isLeaf: true },
]);
const onLoadData: TreeProps["loadData"] = (treeNode) => {
  return new Promise((resolve) => {
    if (treeNode?.dataRef?.children) {
      resolve();
      return;
    }
    setTimeout(() => {
      treeNode.dataRef.children = [
        { title: "Child Node", key: `${treeNode.eventKey}-0` },
        { title: "Child Node", key: `${treeNode.eventKey}-1` },
      ];
      treeData.value = [...treeData.value];
      resolve();
    }, 1000);
  });
};
const checkedKeys = ref<any[]>([]);
const handleCheck = (checkedArr: any, e: any) => {
  console.log(checkedArr, e);
  // if(checkedArr.includes(0)){

  // }
  console.log(checkedKeys.value);
};
</script>

<style lang="scss" scoped></style>
