<template>
  <div>
    <el-button type="primary" @click="willAdd">添加</el-button>

    <v-list @edit="edit"></v-list>

    <v-from :info="info" ref="form"></v-from>
  </div>
</template>
<script>
import { mapGetters, mapActions } from "vuex";
import vList from "./components/from";
import vFrom from "./components/list";
import { reqUserList, reqUserCount } from "../../utils/http";
export default {
  components: {
    vList,
    vFrom,
  },
  data() {
    return {
      info: {
        isshow: false,
        title: "添加分类",
      },
    };
  },
  computed: {
    ...mapGetters({}),
  },
  methods: {
    ...mapActions({}),
    //点击了添加按钮
    willAdd() {
      this.info = {
        isshow: true,
        title: "添加分类",
      };
    },
    //编辑
    edit(id) {
      this.info = {
        isshow: true,
        title: "编辑分类",
      };
      this.$refs.from.getOne(id);
    },
  },
  mounted() {},
};
</script>
<style scoped>
</style>