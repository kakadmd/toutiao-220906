<template>
  <div>
    <!-- 二级路由 -->
    <!-- 左滑进入 -->
    <transition name="van-slide-left" mode="out-in">
      <router-view></router-view>
    </transition>
    <!-- 导航区 -->
    <!-- 路由模式：拿item的to属性和当前路由的path对比，如果一样就高亮 -->
    <van-tabbar route class="tabbar">
      <van-tabbar-item to="/ ">
        <template #icon>
          <span class="toutiao toutiao-shouye"></span>
          <span class="text">首页</span>
        </template>
      </van-tabbar-item>
      <van-tabbar-item to="/video">
        <template #icon>
          <span class="toutiao toutiao-shipin"></span>
          <span class="text">视频</span>
        </template>
      </van-tabbar-item>
      <van-tabbar-item to="/qa">
        <template #icon>
          <span class="toutiao toutiao-wenda"></span>
          <span class="text">问答</span>
        </template>
      </van-tabbar-item>
      <van-tabbar-item to="/profile">
        <template #icon>
          <span class="toutiao toutiao-wode"></span>
          <span class="text">{{ isLogin ? '我的' : '未登录' }}</span>
        </template>
      </van-tabbar-item>
    </van-tabbar>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
  data() {
    return {
      active: 0
    }
  },
  computed: {
    ...mapGetters(['isLogin'])
  }
}
</script>

<style lang="less" scoped>
:deep(.tabbar) {
  .van-tabbar-item__icon {
    display: flex;
    height: 100%;
    flex-direction: column; // 主轴换方向
    align-items: center; // 文本居中
    justify-content: space-evenly;
  }
  .toutiao {
    font-size: 40px;
  }
  .text {
    font-size: 30px;
  }
}
</style>
