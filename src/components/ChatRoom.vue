<template>
  <div class="container">
    <row class="row row-cols-2 justify-content-center">
      <!-- 學生對話窗 -->
      <section class="w-40 position-relative bg-chatroom-header border chatroom-h px-0 me-5">
        <!-- 對話的對象 -->
        <header>
          <h2 class="chatroom-title text-light text-center lh-base py-2">
            學生
            <a href="javascript:;" class="position-absolute end-0 border-start ps-3 me-3 ">
              <img src="../assets/chatroom/設定圖標.png" alt="設定圖標" height="40">
            </a>
          </h2>
        </header>

        <!-- 對話內容 -->
        <div class="container my-4">
          <div v-for="(val, index) in chat" :key="`${val.content}${index}`" class="d-flex lh-lg my-3 mb-3">
            <div class="w-20 d-flex align-items-center">
              <img src="../assets/chatroom/默認大頭貼.png" alt="默認大頭貼" width="20" height="20" class="me-1">
              <span>{{ val.name }}</span>
            </div>
            <span class="w-80 position-relative border-0 rounded-1 bg-light p-2"
                :class="{'bg-myChar': val.name==='小華'}">
              {{ val.content }}
              <!-- 對話氣泡三角形 -->
              <span class="triangle" :class="{'triangle-myChar': val.name==='小華'}"></span>
            </span>
          </div>
        </div>

        <!-- 文字輸入列表 -->
        <footer class="w-100 bg-chatroom-footer position-absolute bottom-0 h-60px">
          <div class="d-flex align-items-center justify-content-center h-100">
            <textarea cols="45" rows="1" class="fs-2 ps-2"></textarea>
            <button type="button" class="btn btn-lg btn-primary ms-2">送出</button>
          </div>
        </footer>
      </section>

      <!-- 老師對話窗 -->
      <section class="w-40 position-relative bg-chatroom-header border chatroom-h px-0">
        <!-- 對話的對象 -->
        <header>
          <h2 class="chatroom-title text-light text-center lh-base py-2">
            老師
            <a href="javascript:;" class="position-absolute end-0 border-start ps-3 me-3 ">
              <img src="../assets/chatroom/設定圖標.png" alt="設定圖標" height="40">
            </a>
          </h2>
        </header>

        <!-- 對話內容 -->
        <div class="container my-4">
          <div v-for="(val, index) in chat" :key="`${val.content}${index}`" class="d-flex lh-lg my-3">
            <div class="w-20 d-flex align-items-center">
              <img src="../assets/chatroom/默認大頭貼.png" alt="默認大頭貼" width="20" height="20" class="me-1">
              <span>{{ val.name }}</span>
            </div>
            <span class="w-80 position-relative border-0 rounded-1 bg-light p-2" :class="{'bg-myChar': val.name==='王老師'}">
              {{ val.content }}
              <!-- 對話氣泡三角形 -->
              <span class="triangle" :class="{'triangle-myChar': val.name==='王老師'}"></span>
            </span>
          </div>
        </div>

        <!-- 文字輸入列表 -->
        <footer class="w-100 bg-chatroom-footer position-absolute bottom-0 h-60px">
          <div class="d-flex align-items-center justify-content-center h-100">
            <textarea cols="45" rows="1" class="fs-2 ps-2"></textarea>
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
      isLoading: false,
      chat: [
        {
          status: 'teacher',
          name: '王老師',
          content: '你好，我是小明老師，記得打卡簽到唷!!'
        },
        {
          status: 'teacher',
          name: '王老師',
          content: '這是報到的 QR Code!'
        },
        {
          status: 'student',
          name: '小華',
          content: '謝謝老師，我想順便請問作業是寫到第二章節就可以嗎?目前正準備開始寫作業!'
        },
        {
          status: 'teacher',
          name: '王老師',
          content: '沒有錯，記得要準時繳交唷!!'
        },
        {
          status: 'student',
          name: '小華',
          content: '謝謝老師，我已經開始蒐集作業資料，順便整理了一下筆記，希望明天可以準時提交作業。'
        },
        {
          status: 'teacher',
          name: '王老師',
          content: '不客氣^^'
        }
      ]
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
.w-20 {
  width: 20%;
}
.w-40 {
  width: 40%;
}
.w-80 {
  max-width: 80%;
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
.rounded-1 {
  border-radius: 15px !important;
}
.bg-myChar {
  background-color: #84E148 !important;
}
//* 對話氣泡三角形
.triangle::before {
  position: absolute;
  top: 50%;
  left: -12px;
  transform: translateY(-50%);
  display: inline-block;
  content: '';
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 10px 15px 10px 0;
  border-color: transparent rgba(var(--bs-light-rgb), var(--bs-bg-opacity)) transparent transparent;
}
.triangle-myChar::before {
  border-color: transparent #84E148 transparent transparent;
}
</style>
