<template>
  <div>
    <TypeNav></TypeNav>
    <ListContainer></ListContainer>
    <Recommend></Recommend>
    <Rank></Rank>
    <Like></Like>
    <Floor v-for="floor in floorList" :key="floor.id" :list="floor"></Floor>
    <Brand></Brand>
  </div>
</template>

<script>
//非路由组件在使用的时候分为三大步：定义、注册、使用
import ListContainer from "@/pages/Home/ListContainer";
import Recommend from "@/pages/Home/Recommend";
import Rank from "@/pages/Home/Rank";
import Like from "@/pages/Home/Like";
import Floor from "@/pages/Home/Floor";
import Brand from "@/pages/Home/Brand";
import {mapState} from 'vuex'

export default {
  name: "",
  components: {ListContainer, Recommend, Rank, Like, Floor, Brand},
  mounted() {
    //派发action,获取floor组件的数据
    this.$store.dispatch("getFloorList");
    this.$store.dispatch('getUserInfo');
  },
  computed: {
    ...mapState({
      floorList: (state)=>state.home.floorList
    })
  }
}
</script>

<style scoped>

</style>