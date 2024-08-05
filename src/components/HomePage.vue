<template>
  <div class="home">
    <div class="content">
      <img src="@/assets/photo.jpg" alt="Your Photo" class="photo" />
      <div class="text">
        <pre v-html="displayedText" class="code"></pre>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  data() {
    return {
      fullText: `
        // About Me
        const name = "Марков Альберт Дмитриевич, 24 года";
        const profession = "Ввиды работ: работал год в smm(компьютерный клуб), нынешнее место работы ОАК "Авиастар" fullstack разработчик";
        const bio = "Увлекаюсь фотографией и ведосьемкой, нравится изучать что-то новое в работе самое главное чтобы было весело ";
      `,
      displayedText: '',
      typingSpeed: 50,
    };
  },
  mounted() {
    this.typeText();
  },
  methods: {
    typeText() {
      let i = 0;
      const interval = setInterval(() => {
        this.displayedText += this.fullText.charAt(i);
        i++;
        if (i === this.fullText.length) {
          clearInterval(interval);
        }
      }, this.typingSpeed);
    },
  },
}
</script>

<style scoped>
.home {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-color: #f0f0f0;
}

.content {
  text-align: center;
}

.photo {
  width: 600px;
  height: 300px;
  /* border-radius: 50%; */
  margin-bottom: 20px;
}

.code {
  font-family: 'Courier New', Courier, monospace;
  background-color: #282c34;
  color: #61dafb;
  padding: 20px;
  border-radius: 5px;
  white-space: pre-wrap;
  text-align: left;
}
</style>
