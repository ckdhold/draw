<script setup lang="ts">
import { computed } from "vue";
import { useRoute, useRouter } from "vue-router";
import { configRoutesChildren } from "../../router";

const router = useRouter();
const route = useRoute();

// 过滤掉重定向路由，只保留有 meta 的菜单项
const menuList = computed(() => {
  return configRoutesChildren.filter((item) => item.meta);
});

function skip(path: string) {
  router.push(path);
}
// 跳转到工信部备案查询网站
const openBeianLink = (type: string) => {
  if (type === "icp") {
    window.open("https://beian.miit.gov.cn/", "_blank");
  } else if (type === "gongan") {
    window.open("https://beian.mps.gov.cn/#/", "_blank");
  }
};
</script>

<template>
  <div class="flex min-h-[calc(100%-280px)]">
    <ul class="pt-14 m-0 mr-3 w-56 min-w-56 menu bg-base-200">
      <li v-for="item in menuList" :key="item.name">
        <a
          :style="
            item.name === route.name
              ? 'background-color:rgba(12,12,12,0.2)'
              : ''
          "
          @click="skip(item.path)"
        >
          <svg-icon v-if="item.meta?.icon" :name="item.meta.icon" />
          {{ item.meta!.title }}
        </a>
      </li>
    </ul>
    <router-view class="flex-1 mt-5" />
  </div>
  <footer
    class="p-10 rounded footer footer-center bg-base-200 text-base-content"
  >
    <aside>
      <div class="flex gap-2 justify-center items-center">
        <p class="p-0 m-0 text-center">
          Copyright &copy;
          <a
            href="https://www.cked.cn/index.html#/pages/profile/profile"
            target="_blank"
            rel="noopener noreferrer"
            class="font-normal underline text-inherit"
            >www.cked.cn</a
          >&nbsp;All Rights Reserved.
          <a
            href="https://www.cked.cn/index.html#/pages/contact/contact"
            target="_blank"
            rel="noopener noreferrer"
            class="ml-1 font-normal underline text-inherit"
            >意见反馈.</a
          >
          <a
            href="https://www.cked.cn/index.html#/pages/donate/donate"
            target="_blank"
            rel="noopener noreferrer"
            class="ml-1 font-normal underline text-inherit"
            >赞赏.</a
          >
        </p>
        <a
          href="https://github.com/ckdhold/luck#"
          target="_blank"
          rel="noopener noreferrer"
          class="transition-opacity cursor-pointer text-inherit hover:opacity-80"
        >
          <svg-icon name="github" />
        </a>
      </div>
      <div style="cursor: pointer; display: flex">
        <div style="cursor: pointer; display: flex">
          <img
            class="ga-icon"
            src="https://beian.mps.gov.cn/web/assets/logo01.6189a29f.png"
            style="object-fit: contain"
          />
          <span @click="openBeianLink('gongan')" class="beian-link"
            >浙公网安备33011002018531号</span
          >
        </div>
        <div style="cursor: pointer; display: flex">
          <img
            class="ga-icon"
            src="https://gw.alicdn.com/tfs/TB1GxwdSXXXXXa.aXXXXXXXXXXX-65-70.gif"
            style="object-fit: contain"
          />
          <span @click="openBeianLink('icp')" class="beian-link"
            >浙ICP备2025183846号-3</span
          >
        </div>
      </div>
    </aside>
  </footer>
</template>

<style scoped>
.ga-icon {
  width: 16px;
  height: 16px;
  vertical-align: middle;
  margin: 0 5px;
}
</style>
