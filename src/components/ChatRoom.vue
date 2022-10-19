<template>
  <div class="container">
    <row class="row row-cols-2 justify-content-center">
      <!-- 老師對話窗 -->
      <section class="w-40 position-relative bg-chatroom-header border chatroom-h px-0 me-5">
        <header>
          <h2 class="chatroom-title text-light text-center lh-base py-2">
            老師
            <a href="javascript:;" class="position-absolute end-0 border-start ps-3 me-3 ">
              <img src="../assets/chatroom/設定圖標.png" alt="設定圖標" height="40">
            </a>
          </h2>
        </header>

        <!-- 對話框 -->
        <footer class="w-100 bg-chatroom-footer position-absolute bottom-0 h-60px">
          <div class="d-flex align-items-center justify-content-center h-100">
            <textarea cols="45" rows="2"></textarea>
            <button type="button" class="btn btn-lg btn-primary ms-2">送出</button>
          </div>
        </footer>
      </section>
      <!-- 學生對話窗 -->
      <section class="w-40 position-relative bg-chatroom-header border chatroom-h px-0">
        <header>
          <h2 class="chatroom-title text-light text-center lh-base py-2">
            學生
            <a href="javascript:;" class="position-absolute end-0 border-start ps-3 me-3 ">
              <img src="../assets/chatroom/設定圖標.png" alt="設定圖標" height="40">
            </a>
          </h2>
        </header>

       <!-- 對話框 -->
        <footer class="w-100 bg-chatroom-footer position-absolute bottom-0 h-60px">
          <div class="d-flex align-items-center justify-content-center h-100">
            <textarea cols="45" rows="2"></textarea>
            <button type="button" class="btn btn-lg btn-primary ms-2">送出</button>
          </div>
        </footer>

      </section>
    </row>
  </div>

   <IsLoading v-model:active="isLoading"></IsLoading>
</template>

<script>

export default {

  data () {
    return {
      isLoading: false
    }
  },

  watch: {
  },

  methods: {
  },

  mounted () {
  }

}
</script>

<style lang='scss' scope>
.w-40 {
  width: 40%;
}
.bg-chatroom-header {
  background-image: url('../assets/chatroom/LINE聊天室背景.webp');
  background-repeat: no-repeat;
}
.chatroom-title {
  background-color: #3B4555;
}
.chatroom-h {
  height: calc(100vh - 50px);
}
.bg-chatroom-footer {
  background-color: #EBEDEF;
}
.h-60px{
  height: 60px;
}
textarea {
  resize:none;
  width: 80%;
}
</style>
