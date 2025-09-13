<template>
  <section class="main">
    <div class="content">
      <div class="rotate_section" :style="rotateMain"></div>
      <span class="title_content">404</span>
      <span class="title_content-change" :style="rotateStyleChange">404</span>
      <span class="main_text">صفحه مورد نظر یافت نشد</span>
      <div class="btn_content">
        <span class="text_btn">بازگشت به صفحه اصلی</span>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";

const rotateMain = ref({
  top: "50%",
  left: "50%",
  transform: "translate(-50%, -50%)",
});

const rotateStyleChange = ref({
  top: "50%",
  left: "50%",
  transform: "translate(-50%, -50%)",
});

onMounted(() => {
  setInterval(() => {
    const offsetTop = 45 + Math.sin(Date.now() / 750) * 5;
    const offsetLeft = 50 + Math.cos(Date.now() / 750) * 6;
    const translateX = -offsetLeft;
    const translateY = -offsetTop;

    const offsetTopChange = 30 + Math.sin(Date.now() / 750) * 5;
    const offsetLeftChange = 45 + Math.cos(Date.now() / 750) * 5;
    const translateXChange = -offsetLeftChange;
    const translateYChange = -offsetTopChange;

    rotateMain.value = {
      top: offsetTop + "%",
      left: offsetLeft + "%",
      transform: `translate(${translateX}%, ${translateY}%)`,
    };
    rotateStyleChange.value = {
      top: offsetTopChange + "%",
      left: offsetLeftChange + "%",
      transform: `translate(${translateXChange}%, ${translateYChange}%)`,
    };
  }, 16);
});
</script>

<style>
* {
  font-family: IRANSansXFaNum, -apple-system, BlinkMacSystemFont, "Segoe UI",
    "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans",
    "Helvetica Neue", sans-serif;
}

html,
body {
  height: 100%;
  margin: 0;
}

.main {
  position: relative;
  overflow: hidden;
  display: flex;
  height: 100vh;
  justify-content: center;
  background-color: #737373;
}

.btn_content {
  background: #22ce83;
  color: white;
  z-index: 111111111;
  font-size: 1.2rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  padding: 15px;
  border-radius: 8px;
}

.content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 15px;
  align-items: center;
}

.main_text {
  text-align: center;
  font-size: 3rem;
  margin-top: 1rem;
  margin-bottom: 1rem;
  font-weight: 400;
  z-index: 111111111;
  color: white;
}

.rotate_section {
  position: absolute;
  background: radial-gradient(40% 40% at 50% 42%, white, #000 35%) !important;
  z-index: 11;
  height: 250vmax;
  width: 250vmax;
  box-shadow: rgba(245, 243, 243, 0.56) 0px 22px 70px 4px;
}

.title_content {
  text-align: center;
  font-size: 18rem;
  line-height: 18rem;
  color: #737373;
  z-index: 1111111;
}
.title_content-change {
  text-align: center;
  position: absolute;
  font-size: 18rem;
  line-height: 18rem;
  color: black;
  filter: blur(1.5vmin);
  z-index: 111111;
}
</style>