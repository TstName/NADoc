<template>
  <div></div>
</template>
<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  setup(props) {
    console.log(props);
    const menu = ref<Object[]>([
      {
        title: "设备数据",
        children: [
          {
            title: "iPhon 6.0Plus",
            children: ["增加", "删除", "修改", "查找"],
          },
          {
            title: "OPPO A80",
            children: ["增加", "删除"],
          },
        ],
      },
    ]);
    return {
      menu,
    };
  },
});
</script>

<style scoped>
</style>