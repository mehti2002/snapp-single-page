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
  transform: "translate(-50%, -50%)",
});

const rotateStyleChange = ref({
  transform: "translate(-50%, -50%)",
});

onMounted(() => {
  const animate = () => {
    const offsetX = Math.cos(Date.now() / 800) * 5;
    const offsetY = Math.sin(Date.now() / 1000) * 5;
    rotateMain.value = {
      top: "50%",
      left: "50%",
      transform: `translate(calc(-50% + ${offsetX}%), calc(-50% + ${offsetY}%))`,
    };

    const textOffsetX = Math.cos(Date.now() / 600) * 3;
    const textOffsetY = Math.sin(Date.now() / 700) * 3;
    rotateStyleChange.value = {
      top: "50%",
      left: "50%",
      transform: `translate(calc(-50% + ${textOffsetX}%), calc(-50% + ${textOffsetY}%))`,
    };

    requestAnimationFrame(animate);
  };

  animate();
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
  z-index: 10;
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
  z-index: 10;
  color: white;
}

@media (max-width: 1024px) {
  .main_text {
    font-size: 2rem;
  }
}

.rotate_section {
  position: absolute;
  top: 50%;
  left: 50%;
  background: radial-gradient(40% 40% at 50% 42%, white, #000 35%);
  height: 250vmax;
  width: 250vmax;
  transform: translate(-50%, -50%);
  z-index: 1;
  box-shadow: rgba(245, 243, 243, 0.56) 0px 22px 70px 4px;
}

.title_content {
  text-align: center;
  font-size: 18rem;
  line-height: 18rem;
  color: #737373;
  z-index: 5;
  position: relative;
}

@media (max-width: 1024px) {
  .title_content {
    font-size: 12rem;
  }
}

.title_content-change {
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  font-size: 18rem;
  line-height: 18rem;
  color: black;
  filter: blur(1.5vmin);
  z-index: 2;
  transform: translate(-50%, -50%);
}

@media (max-width: 1024px) {
  .title_content-change {
    font-size: 12rem;
  }
}
</style>
