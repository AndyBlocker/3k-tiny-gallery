<template>
  <div class="title-container" :style="{ '--color': color }">
    <div class="main-title-box">
      <h2 class="main-title">{{ mainTitle }}</h2>
    </div>
    <h2 class="sub-title">{{ subTitle }}</h2>
  </div>
</template>

<script>
export default {
  name: 'ParaTitle',
  props: {
    mainTitle: String,
    subTitle: String,
    color: String  // 允许从外部传入背景颜色
  }
}
</script>

<style scoped>
.title-container {
  display: flex; /* 使用flexbox布局 */
  flex-direction: column; /* 子元素垂直排列 */
  justify-content: center; /* 垂直居中 */
  align-items: center; /* 水平居中 */
  text-align: center;
  font-family: 'Arial', sans-serif;
  position: relative;
  height: 50vh; /* 容器高度，保持响应性 */
  width: 100%; /* 容器宽度，覆盖父元素 */
}

.main-title-box {
  background-color: white;
  color: black;
  border: 2px solid var(--color #9c67b5); /* 主标题边框颜色 */
  transform: rotate(-10deg);
  display: inline-block;
  padding: 1vw 2vw;
  position: relative;
  transform: translateX(-50%) rotate(-10deg);
  z-index: 2; /* 确保主标题在上层 */
}

.main-title {
  font-size: 3vw;
  margin: 0;
}

.sub-title {
  font-size: 2vw;
  background-color: var(--color #9c67b5); /* 暗红色背景，模仿图片 */
  color: black;
  padding: 0.5vw 1vw;
  display: inline-block;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  z-index: 1; /* 确保副标题在下层 */
}
</style>
