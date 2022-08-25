<template>
  <div>
    <span v-for="(item, index) in arr" :key="index"
      ><input type="checkbox" :value="item" v-model="newArr" />{{ item }}</span
    >
    <p>你选中的元素累计和是{{ num }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: [9, 15, 19, 25, 29, 31, 48, 57, 62, 79, 87],
      newArr: [],
    };
  },
  computed: {
    num() {
      return this.newArr.reduce((sum, item) => {
        return (sum += item);
      }, 0);
    },
  },
};
</script>

<style></style>
