<template>
  <div>
    <el-button type="primary" @click="willAdd">添加</el-button>

    <!-- 绑定自定义事件init -->
    <!-- 绑定edit事件 -->
    <v-list :list="list" @init="init" @edit="edit"></v-list>

    <!-- 传递info给form  -->
    <!-- 绑定自定义事件init -->
    <v-form :info="info" @init="init" ref="form"></v-form>
  </div>
</template>
<script>
import { mapGetters, mapActions } from "vuex";
import vList from "./components/list.vue"
import vForm from "./components/form.vue"
import {reqRoleList} from "../../utils/http"
export default {
  components:{
    vList,
    vForm
  },
  data(){
    return {
      // 初始值 弹框数据
      info:{
        isshow:false,
        title:"添加角色"
      },
      //列表数据初始值
      list:[]
    }
  },
  computed: {
    ...mapGetters({})
  },
  methods: {
    ...mapActions({}),
    //点击了添加按钮
    willAdd(){
      this.info={
        isshow:true,
        title:"添加角色"
      }
    },
    //发请求
    init(){
      reqRoleList().then(res=>{
        this.list=res.data.list
      })
    },
    // 编辑
    edit(id){
      this.info={
        isshow:true,
        title:"编辑角色"
      }
      this.$refs.form.getOne(id)
    }
  },
  mounted() {
    //一进来发请求
    this.init()
  }
};
</script>
<style scoped>
</style>