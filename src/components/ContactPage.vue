<template>
  <div class="contact" @click="toggleOpen">
    <div :class="['door', { open: isOpen }]">
      <div class="phrase">Как со мной связаться?</div>
      <div class="links" v-if="isOpen">
        <a href="https://github.com/Fugilove" target="_blank">GitHub</a>
        <a href="https://vk.com/i_love_fine" target="_blank">ВКонтакте</a>
        <a href="https://ulyanovsk.hh.ru/applicant/settings?from=header_new&hhtmFromLabel=header_new&hhtmFrom=main" target="_blank">HH</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContactPage',
  data() {
    return {
      isOpen: false
    };
  },
  methods: {
    toggleOpen() {
      this.isOpen = !this.isOpen;
    }
  }
}
</script>

<style scoped>
.contact {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-color: #f0f0f0;
  cursor: pointer;
}

.door {
  position: relative;
  width: 600px;
  height: 200px;
  background-color: #007bff;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  transition: width 1s, height 1s;
}

.door.open {
  width: 1200px;
  height: 400px;
}

.phrase {
  font-size: 1.5rem;
  transition: opacity 1s;
}

.door.open .phrase {
  opacity: 0;
}

.links {
  position: absolute;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

.links a {
  color: white;
  font-size: 1rem;
  text-decoration: none;
}

.links a:hover {
  text-decoration: underline;
}
</style>
