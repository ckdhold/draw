<script setup lang="ts">
import localforage from 'localforage';
import { onMounted, ref } from 'vue';

const props = defineProps({
  imgItem: {
    type: Object,
    default: () => ({}),
  },
});
const imageDbStore = localforage.createInstance({
  name: 'imgStore',
});

const imgUrl = ref('');

async function getImageStoreItem(item: any): Promise<string> {
  let image = '';
  if (item.url === 'Storage') {
    const key = item.id;
    image = (await imageDbStore.getItem(key)) as string;
  } else {
    // 确保路径是相对于根目录的，在hash路由模式下正确解析
    image = item.url.startsWith('/') ? item.url : `./${item.url}`;
  }
  console.log('image', image);
  return image;
}

onMounted(async () => {
  const image = await getImageStoreItem(props.imgItem)
  imgUrl.value = image
})

function handleImageError() {
  // 图片加载失败时使用兜底图片
  imgUrl.value = 'https://cfmoto-evow.oss-cn-hangzhou.aliyuncs.com/AdminFiles/ports/doudi.svg'
}
</script>

<template>
  <img :src="imgUrl" alt="Image" class="object-cover h-full rounded-xl" @error="handleImageError" />
</template>

<style lang="scss" scoped></style>
