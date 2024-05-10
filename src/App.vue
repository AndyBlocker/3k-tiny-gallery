<template>
  <div class="chat-container">
    <ChatMessage
      v-for="message in messages"
      :key="message.id"
      :name="message.name"
      :icon="message.icon"
      :isRight="message.isRight"
      :content="message.content"
      :color="message.color"
    />
  </div>
</template>



<script>
// import ParaTitle from './components/ParaTitle.vue';
import ChatMessage from './components/ChatMessage.vue';

export default {
  name: 'App',
  components: {
    // ParaTitle,
    ChatMessage
  },
  data() {
    return {
      messages: [
        {
          id: 1,
          name: '一车面包人',
          icon: require('@/assets/middle_cat.jpg'),
          isRight: false,
          content: '一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人一车面包人!',
          color : "#9c67b5"
        },
        {
          id: 2,
          name: '另一车面包人',
          icon: require('@/assets/u_know_who.png'),
          isRight: true,
          content: '另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人另一车面包人！',
          color : "#ff9d95"
        }
      ]
    }
  }
}
</script>

<style>
.chat-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  margin-top: 50px;
}
body {
  background-color: #161616;
}
</style>
