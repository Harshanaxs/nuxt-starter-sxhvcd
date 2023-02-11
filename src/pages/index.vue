<template>
  <div>
    11111
    <div>
      <van-cell title="Select Date Range" :value="date" @click="show = true" />
      <van-calendar v-model:show="show" type="range" @confirm="onConfirm" />
    </div>
    <van-tabbar v-model="active">
      <van-tabbar-item icon="home-o">标签</van-tabbar-item>
      <van-tabbar-item icon="search">标签</van-tabbar-item>
      <van-tabbar-item icon="friends-o">标签</van-tabbar-item>
      <van-tabbar-item icon="setting-o">标签</van-tabbar-item>
    </van-tabbar>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const date = ref('');
    const show = ref(false);

    const formatDate = (date) => `${date.getMonth() + 1}/${date.getDate()}`;
    const onConfirm = (values) => {
      const [start, end] = values;
      show.value = false;
      date.value = `${formatDate(start)} - ${formatDate(end)}`;
    };

    return {
      date,
      show,
      onConfirm,
    };
  },
};
</script>
