<template>
  <div>
    <h1>사용자 리스트</h1>
    <ul>
      <li v-for="item in list" :key="item">{{ item }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      list: ['하나', '둘', '셋'],
    };
  },
  mounted() {
    axios.get('http://localhost:8083/api/users').then((res) => {
      console.log(res.data);
      const names = res.data.map((item) => {
        return item.name;
      });
      this.list = names;
    });
  },
};
</script>

<style></style>
