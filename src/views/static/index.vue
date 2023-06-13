<template>
  <el-row>
    <el-col :span="24" class="navbar">
      <el-menu
        mode="horizontal"
        active-text-color="#e60012"
        background-color="#3F4FA2"
        default-active="1"
        text-color="#fff"
        @open="handleOpen"
        @close="handleClose"
      >
        <el-menu-item index="/userLog" @click="goTo('/userLog')">
          用户日志
        </el-menu-item>
        <el-menu-item index="/userLevel" @click="goTo('/userLevel')">
          用户等级
        </el-menu-item>
        <el-menu-item index="/user" @click="goTo('/user')">
          用户管理
        </el-menu-item>
        <el-menu-item index="/userArticle" @click="goTo('/userArticle')">
          用户文章
        </el-menu-item>
        <el-menu-item index="/memorabilia" @click="goTo('/memorabilia')">
          用户大事件
        </el-menu-item>
      </el-menu>
    </el-col>

    <el-col :span="21">
      <router-view></router-view>
    </el-col>
  </el-row>
</template>

<script>
import { defineComponent } from "vue";
import { useUserStore } from "../../store/user";
import { useRouter } from 'vue-router';

export default defineComponent({
  setup() {
    const store = useUserStore();
    const { count } = store;
    const router = useRouter();

    const handleOpen = (key, keyPath) => {
      console.log(key, keyPath);
    };

    const handleClose = (key, keyPath) => {
      console.log(key, keyPath);
    };

    const goTo = (path) => {
      router.replace(path);
    };

    return {
      count,
      handleOpen,
      handleClose,
      goTo,
    };
  },
});
</script>


<style lang="scss" scoped>
.navbar {
  background-color: #9da9e7;
  height: 60px;
  line-height: 60px;
}

.el-menu {
  background-color: #8798ee;
  color: #fff;
}

.el-menu-item {
  height: 60px;
  line-height: 60px;
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.el-menu-item:hover,
.el-menu-item.is-active {
  background-color: #7285e6;
}

.el-menu--horizontal {
  display: flex;
  align-items: center;
}
</style>