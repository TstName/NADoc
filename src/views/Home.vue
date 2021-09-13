<template>
  <a-layout>
    <a-layout-sider
      breakpoint="lg"
      collapsed-width="0"
      @collapse="onCollapse"
      @breakpoint="onBreakpoint"
    >
      <div class="logo">NodeJS API</div>
      <a-menu theme="dark" mode="inline" v-model:selectedKeys="selectedKeys">
        <template v-for="(item, index) in menu">
          <a-menu-item
            v-if="item.children && item.children.length < 1"
            :key="index"
          >
            <span class="nav-text">{{ item.title }}</span>
          </a-menu-item>
          <a-sub-menu v-else :key="index + ''">
            <template #title>{{ item.title }}</template>
            <template v-for="(items, indexs) in item.children">
              <a-menu-item
                v-if="items.children && items.children.length < 1"
                :key="index + '-' + indexs"
                >{{ items.title }}</a-menu-item
              >
              <a-sub-menu
                v-else
                :key="index + '-' + indexs"
                :title="items.title"
              >
                <a-menu-item
                  v-for="(itemss, indexss) in items.children"
                  :key="index + '-' + indexs + '-' + indexss"
                  >{{ itemss }}</a-menu-item
                >
              </a-sub-menu>
            </template>
          </a-sub-menu>
        </template>
      </a-menu>
    </a-layout-sider>
    <a-layout>
      <a-layout-header :style="{ background: '#fff', padding: 0 }" />
      <a-layout-content :style="{ margin: '24px 16px 0' }">
        <div
          :style="{ padding: '24px', background: '#fff', minHeight: '360px' }"
        >
          content
        </div>
      </a-layout-content>
      <a-layout-footer style="text-align: center">
        NodeJS ©2021 Created by Elegant、小太爷
      </a-layout-footer>
    </a-layout>
  </a-layout>
</template>

<script lang="ts">
import {
  UserOutlined,
  VideoCameraOutlined,
  UploadOutlined,
} from "@ant-design/icons-vue";
import { defineComponent, ref } from "vue";
export default defineComponent({
  components: {
    UserOutlined,
    VideoCameraOutlined,
    UploadOutlined,
  },
  data() {
    return {
      menu: [
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
      ],
    };
  },
  setup() {
    const onCollapse = (collapsed: boolean, type: string) => {
      console.log(collapsed, type);
    };

    const onBreakpoint = (broken: boolean) => {
      console.log(broken);
    };

    return {
      selectedKeys: ref<string[]>([]),
      onCollapse,
      onBreakpoint,
    };
  },
});
</script>
<style scoped>
.ant-layout {
  height: 100%;
}
.logo {
  height: 32px;
  color: white;
  font-weight: 700;
  font-size: 18px;
  line-height: 32px;
  background: rgba(255, 255, 255, 0.2);
  margin: 16px;
}

.site-layout-sub-header-background {
  background: #fff;
}

.site-layout-background {
  background: #fff;
}

[data-theme="dark"] .site-layout-sub-header-background {
  background: #141414;
}
</style>