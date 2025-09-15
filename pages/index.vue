<template>
  <section class="main">
    <div class="content">
      <span class="title_content">404</span>
      <span class="title_content-main">404</span>
      <div class="container_navigate-container">
        <div class="container_navigate-section">
          <div class="container_navigate"></div>
        </div>
      </div>

      <span class="main_text">صفحه مورد نظر یافت نشد</span>

      <div class="btn_content">
        <span class="text_btn">بازگشت به صفحه اصلی</span>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const navigatePoints = [
  { x: 71, y: -45 },
  { x: 37, y: -10 },
  { x: 81, y: -61 },
];

function lerp(a, b, t) {
  return a + (b - a) * t;
}

let animationFrameId;
let currentIndex = 0;
let nextIndex = 1;
let progress = 0;
const speed = 0.002;

const animate = () => {
  progress += speed;
  if (progress >= 1) {
    progress = 0;
    currentIndex = nextIndex;
    nextIndex = (nextIndex + 1) % navigatePoints.length;
  }

  const current = navigatePoints[currentIndex];
  const next = navigatePoints[nextIndex];

  const navigateX = Math.round(lerp(current.x, next.x, progress));
  const navigateY = Math.round(lerp(current.y, next.y, progress));

  document.documentElement.style.setProperty("--navigate-x", navigateX);
  document.documentElement.style.setProperty("--navigate-y", navigateY);

  const offsetX = navigateX * 0.05 + "%";
  const offsetY = navigateY * 0.05 + "%";
  document.documentElement.style.setProperty("--offset-x", offsetX);
  document.documentElement.style.setProperty("--offset-y", offsetY);

  animationFrameId = requestAnimationFrame(animate);
};

onMounted(() => {
  animate();
});

onBeforeUnmount(() => {
  cancelAnimationFrame(animationFrameId);
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
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: #737373;
  color: #fafafa;
  perspective: 1200px;
  overflow: hidden;
}

.btn_content {
  background: #22ce83;
  color: white;
  font-size: 1.2rem;
  cursor: pointer;
  display: flex;
  z-index: 11;
  align-items: center;
  padding: 15px;
  border-radius: 8px;
}

.content {
  display: flex;
  position: relative;
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

.container_navigate-container {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  overflow: hidden;
  z-index: 1;
}

.container_navigate-section {
  height: 250vmax;
  width: 250vmax;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.container_navigate {
  animation: navigate 2s ease-in-out infinite alternate-reverse;
  height: 100%;
  width: 100%;
  transform-origin: 50% 30%;
  transform: rotate(calc(var(--navigate-x) * -0.25deg));
  background: radial-gradient(40% 40% at 50% 42%, #7a7a7a, #000 35%);
}

.title_content {
  text-align: center;
  font-size: 18rem;
  line-height: 18rem;
  z-index: 1111111;
  position: relative;
  color: #7a7a7a;
}

.title_content-main {
  position: absolute;
  font-size: 18rem;
  line-height: 18rem;
  top: 0;
  left: 0;
  color: #000;
  filter: blur(1.5vmin);
  z-index: 133;
  transform: scale(1.05) translate3d(0, 12%, -10vmin)
    translate(
      calc((var(--navigate-x, 0) * 0.05) * 1%),
      calc((var(--navigate-y) * 0.05) * 1%)
    );
  animation: navigate 2s ease-in-out infinite alternate;
}

@keyframes navigate {
  0% {
    --navigate-x: -100;
    --navigate-y: -100;
  }
  50% {
    --navigate-y: 0;
  }
  100% {
    --navigate-y: -100;
    --navigate-x: 100;
  }
}

@property --navigate-x {
  syntax: "<integer>";
  initial-value: 0;
  inherits: false;
}

@property --navigate-y {
  syntax: "<integer>";
  initial-value: 0;
  inherits: false;
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
  filter: blur(1.5vmin);
  transform: translate(-50%, -50%)
    translate(var(--offset-x, 0), var(--offset-y, 0));
  background: radial-gradient(#e6e6e6, #7a7a7a 45%);
  -webkit-background-clip: text;
  color: transparent;
}

@media (max-width: 1024px) {
  .title_content-main {
    font-size: 12rem;
  }
}
</style>
