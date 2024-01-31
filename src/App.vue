<template>
  <div id="app">
    <Header/>
    <transition name="fade" mode="out-in">
      <router-view class="view"></router-view>
    </transition>
    <Footer/>
  </div>
</template>

<script lang="ts">
import 'ant-design-vue/dist/antd.less'
import { Component, Vue } from 'vue-property-decorator'
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'

@Component({
  components: {
    Header,
    Footer,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700;900&display=swap');
#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #fafbfd;
  min-height: 100vh;
  color: #2c3e50;
}
.view {
  min-height: 65vh;
}
.card {
  padding: 20px;
  background: white;
  box-shadow: 0 8px 18rem rgba(189, 197, 209, 0.2);
  border-radius: 6px;
  border: 1px solid #e9ecef;

  .title {
    font-size: 16px;
    margin-bottom: 5px;
    font-weight: 500;
  }
}
</style>
