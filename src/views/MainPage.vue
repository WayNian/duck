<template>
  <div class="layout">
    <div>
      <Menu
        mode="horizontal"
        :active-name="getActiveName"
        @on-select="onSelect"
      >
        <Row>
          <Col
            :xs="{ span: 0}"
            :sm="{ span: 0}"
            :lg="{ span: 5 }"
          >
          <div class="layout-logo">
            <img
              src="../assets/keda.png"
              title="waynian"
              @click="goManageBlog"
            >
          </div>
          </Col>
          <Col
            :xs="{ span: 0}"
            :sm="{ span: 0}"
            :lg="{ span: 9, offset:10}"
          >
          <div class="layout-nav">
            <MenuItem name="index"> 首页
            </MenuItem>
            <MenuItem name="blog-list"> 博客
            </MenuItem>
            <MenuItem name="message"> 留言板
            </MenuItem>
            <MenuItem name="tools"> 小工具
            </MenuItem>
            <MenuItem name="about"> 关于
            </MenuItem>
          </div>
          </Col>
        </Row>
      </Menu>
    </div>
    <div>
      <router-view></router-view>
    </div>
    <div class="footer">
      <!-- 已默默运行{{}} -->
    </div>
    <BackTop></BackTop>
  </div>
</template>
<script>
export default {
  data() {
    return {};
  },
  computed: {
    getActiveName() {
      let that = this;
      return that.$route.path.slice(1);
    }
  },
  mounted() {
    this.getRunTime();
  },
  methods: {
    onSelect(name) {
      //页面跳转
      let that = this;
      switch (name) {
        case "index":
          that.$router.push("/index");
          break;
        case "blog-list":
          that.$router.push("/blog-list");
          break;
        case "message":
          that.$router.push("/message");
          break;
        case "tools":
          that.$router.push("/tools");
          break;
        case "about":
          that.$router.push("/about");
          break;
        default:
          that.$router.push("/404");
          break;
      }
    },
    goManageBlog() {
      this.$router.push("/admin/create-blog");
    },
    getRunTime() {
      // let that = this
      // let createTime = new Date('2018/09/26 13:58')
      // let empDate = Date.now() - createTime
      // let year = empDate/ (1000 * 60 * 24)
      // console.log(empDate/ (1000 * 60));
    }
  }
};
</script>
<style lang="scss">
@import "../assets/icon/iconfont.css"; // 引用 iconfont.css
.layout {
  position: relative;
  overflow: hidden;
}
.ivu-menu-light {
  position: fixed;
  top: 0;
  width: 100%;
  background-color: rgba($color: #fff, $alpha: 0.8);
}
.ivu-layout-header {
  background-color: #fff;
  color: #6bc20d;
  font-size: 30px;
}
.ivu-layout-header {
  padding: 0;
}
.layout-logo {
  width: 50px;
  height: 50px;
  float: left;
  position: relative;
  left: 40px;
  img {
    width: 100%;
  }
}
.ivu-menu-item {
  margin-right: 20px;
}
.ivu-menu-light.ivu-menu-horizontal .ivu-menu-item-active,
.ivu-menu-light.ivu-menu-horizontal .ivu-menu-item:hover {
  color: #209e85;
  border-bottom: 2px solid #209e85;
}
.layout-nav {
  margin: 0 auto;
  margin-right: 20px;
}
.footer {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px;
  font-size: 16px;
}
</style>
