<template>
  <div class="chat-message" :class="{ 'right': isRight }" :style="{ '--color': color }">
    <div class="icon" ref="iconContainer">
      <img :src="icon" alt="Icon" />
    </div>
    <div class="message-content" ref="messageContent">
      <h4 ref="nameTag">{{ name }}</h4>
      <p>{{ content }}</p>
    </div>
  </div>
</template>


<script>
import rough from 'roughjs';

export default {
  name: 'ChatMessage',
  props: {
    name: String,
    icon: String,
    isRight: Boolean,
    content: String,
    color: String
  },
  mounted() {
    this.$nextTick(() => {
      this.drawRoughBorders(this.$refs.messageContent);
      this.drawRoughBorders(this.$refs.nameTag, true);
      this.drawRoughBorders(this.$refs.iconContainer);
    });
  },
  methods: {
    drawRoughBorders(node, fill = false) {
      const svgElement = document.createElementNS("http://www.w3.org/2000/svg", "svg");
      svgElement.setAttribute('viewBox', `0 0 ${node.offsetWidth} ${node.offsetHeight}`);
      svgElement.setAttribute('width', node.offsetWidth + 'px');
      svgElement.setAttribute('height', node.offsetHeight + 'px');
      const rc = rough.svg(svgElement);
      const options = {
        roughness: fill ? 5: 3,
        stroke: this.color,
        strokeWidth: fill ? 3 : 2,
        fill: fill ? this.color : 'none',
        fillStyle: 'zigzag',
        fillWeight: 3,
        hachureAngle: 110,
        // seed: 1
      };
      const path = rc.rectangle(0, 0, node.offsetWidth, node.offsetHeight, options);
      svgElement.appendChild(path);
      node.appendChild(svgElement);
      svgElement.style.position = 'absolute';
      svgElement.style.top = '0';
      svgElement.style.left = '0';
      svgElement.style.zIndex = '-1';
    }
  }
}
</script>


<style scoped>
.chat-message {
  display: flex;
  align-items: center;
  margin-bottom: 50px;
  width: 80%;
  max-width: 1000px;
}

.message-content {
  flex-grow: 1;
  padding: 10px;
  color: white;
  font-size: 16px;
  overflow: visible;
  position: relative;
  background: transparent;
}

.message-content svg {
  position: absolute;
  /* top: -100; */
  left: 0;
  width: 100%;
  height: 100%;
  overflow: visible;
  z-index: -2;
  /* display: flex; */
}

.message-content h4 {
  margin: 0;
  font-size: 18px;
  /* background-color: var(--color, #9c67b5); */
  top: -25px;
  left: -25px;
  position: absolute;
  display: inline-block;
  transform: rotate(-15deg);
  padding: 10px;
  z-index: 1;
}

.message-content h4 svg {
  z-index: -1;
}

.icon {
  position: relative;  
  width: calc(5.5em + 4px); 
  height: calc(5.5em + 4px);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 20px;
  transform: rotate(-15deg);
  padding: 8px; 
  z-index: 0; 
}

.chat-message .icon img {
  width: 5.5em;
  height: auto;
  display: block;
}


.right .icon {
  order: 1;
  margin-right: 0;
  margin-left: 20px;
}
</style>
