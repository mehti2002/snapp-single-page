<template>
  <section class="main">
    <div class="content">
      <span class="title_content">404</span>
      <span class="main_text">صفحه مورد نظر یافت نشد</span>
      <div class="btn_content">
        <span class="text_btn">بازگشت به صفحه اصلی</span>
      </div>
    </div>
  </section>
</template>

<script setup>
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
  display: flex;
  height: 100vh;
  justify-content: center;
  background-color: black;
}

.btn_content {
  background: #22ce83;
  color: white;
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
  color: white;
}

.title_content {
  text-align: center;
  font-size: 18rem;
  line-height: 18rem;
  color: #838996;
}
</style>