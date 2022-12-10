<script setup>
import Sidebar from './components/Sidebar.vue'
import Main from './components/Main.vue'
</script>

<template>
  <div class="main">
    <div class="header">
      <span class="header_title">Жилфонд</span>
      <span class="header_client">Пользователь</span>
    </div>
    <div class="main_module">
      <Sidebar class="h" />
      <Main class="h" />
    </div>
  </div>

</template>

<script>
export default {
  components: [Sidebar, Main],
}
</script>


<style lang="scss" scoped>
.main {
  box-sizing: border-box;
  padding: 2% 3%;
  height: 100vh;
  background: #F5F5F5;
  display: flex;
  flex-direction: column;
}

.header {
  display: flex;
  justify-content: space-between;
  margin: 30px 0;

  .header_title {
    font-style: normal;
    font-weight: 800;
    font-size: 32px;
    line-height: 39px;
    color: #E31F24;

  }

  .header_client {
    font-weight: 400;
    font-size: 16px;
    line-height: 20px;
    color: #333333;
  }
}


.main_module {
  background: #FDFDFD;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  color: black;
  display: flex;
  height: 90vh;
  width: 100%;
  max-height: 90vh;
}

.h {
  max-height: 72vh;
}
</style>
