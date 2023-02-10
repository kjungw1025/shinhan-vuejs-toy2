<template>
  <div>
    <!-- <div>news</div> -->
    <list-item :listData="list"></list-item>
  </div>
</template>

<script>
// import axios from 'axios'; axios 통신 장치는 필요없어짐
import ListItem from '../components/ListItem.vue';

export default {
  // data() {
  //   return {
  //     list: [], list()로 가져오므로 필요없음
  //   }
  // },
  components: { ListItem },
  computed: {
    list() {
      return this.$store.state.list;
    }
  },
  created() {
    this.$store.dispatch('FETCH_LIST', 'news');
  },
}
</script>

<style> 
</style>