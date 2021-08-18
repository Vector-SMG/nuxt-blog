<template>
  <div class="header-container">
    <div class="logo" @click="goHome()">朝花夕拾</div>
    <nav>
      <ul>
        <li
          v-for="(item, index) in navs"
          @click="navClick(index, item)"
          :key="index"
        >
          <div
            class="nav-title"
            :class="{ 'nav-title-checked': currentClickIndex == index }"
          >
            {{ item.name }}
          </div>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {
      navs: [
        {
          name: '首页',
          route: '/',
        },
        {
          name: '项目',
          route: '/project',
        },
        {
          name: '博客',
          route: '/blog',
        },
        {
          name: '关于',
          route: '/about',
        },
      ],
      currentClickIndex: 0,
    }
  },
  methods: {
    navClick(index, item) {
      this.currentClickIndex = index
      this.$router.push({
        path: item.route,
      })
    },
    goHome() {
      this.$router.push({ path: '/' })
    },
  },
}
</script>

<style>
.header-container {
  width: 100%;
  height: 240px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #18191b;
  padding: 80px;
  position: fixed;
  z-index: 2000;
  top: 0px;
  background: white;
}
.header-container .logo {
  font-weight: 700;
  font-size: 25px;
  height: 50px;
  writing-mode: vertical-rl;
  writing-mode: tb-lr;
  font-family: Geneva, Tahoma, Verdana, sans-serif;
  font-weight: 400;
  user-select: none;
  cursor: pointer;
  line-height: 28px;
  position: relative;
}

nav {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #18191b;
  color: #a7abb3;
}
nav ul {
  list-style: none;
  display: flex;
  align-items: center;
  padding-inline-start: 0px;
  margin-bottom: 0px;
  padding: 0px 20px;
}
nav ul li {
  flex: 25%;
  padding: 0 20px;
  user-select: none;
  cursor: pointer;
}
.nav-title {
  font-size: 16px;
  width: 16px;
  text-align: center;
  position: relative;
  font-family: Geneva, Tahoma, Verdana, sans-serif;
}
.nav-title-checked::after,
.logo::after {
  content: ' ';
  position: absolute;
  display: block;
  width: 20px;
  height: 20px;
  border: 5px solid #e94328;
  border-radius: 50%;
}
.nav-title-checked::after {
  top: -5px;
  right: -15px;
  background: #18191b;
}
.logo::after {
  top: -5px;
  right: -10px;
  background: white;
}
</style>
