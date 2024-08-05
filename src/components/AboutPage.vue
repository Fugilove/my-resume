<template>
  <div class="about">
    <div class="project" v-for="project in projects" :key="project.id">
      <h2 class="project-title">{{ project.title }}</h2>
      <p class="project-description">{{ project.description }}</p>
      <ul class="technologies">
        <li v-for="tech in project.technologies" :key="tech">{{ tech }}</li>
      </ul>
      <div v-if="project.id === 1" class="animation" id="taxi-animation">
        <div class="car">
          <div class="car-body"></div>
          <div class="wheel wheel-front"></div>
          <div class="wheel wheel-back"></div>
        </div>
      </div>
      <div v-if="project.id === 2" class="animation" id="work-animation">
        <div class="person person1">
          <div class="head"></div>
          <div class="body"></div>
        </div>
        <div class="person person2">
          <div class="head"></div>
          <div class="body"></div>
        </div>
      </div>
      <div v-if="project.id === 3" class="animation" id="tools-animation">
        <div class="tool tool1">
          <div class="handle"></div>
          <div class="head"></div>
        </div>
        <div class="tool tool2">
          <div class="handle"></div>
          <div class="head"></div>
        </div>
        <div class="tool tool3">
          <div class="handle"></div>
          <div class="head"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AboutPage',
  data() {
    return {
      projects: [
        {
          id: 1,
          title: 'Корпоративное такси',
          description: `
            Полностью велась разработка без ТЗ. Придумывалось всё с нуля и самое главное чтобы это всё работало в локальной сети без интернета.
          `,
          technologies: ['Vue 3 composition api', 'Laravel', 'Oracle', 'Tailwind', 'Vueprime']
        },
        {
          id: 2,
          title: 'Справочник рабочих мест',
          description: `
            Мой первый проект на этой работе. Первый опыт работы с Vue и Laravel.
          `,
          technologies: ['Vue 2', 'Laravel', 'Oracle', 'Tailwind']
        },
        {
          id: 3,
          title: 'Справочник применяемого инструмента',
          description: `
            Мы должны были скопировать функционал учёта складов как у Waldberis или Ozone.
          `,
          technologies: ['Vue 3', 'Laravel', 'Oracle', 'Tailwind', 'Vuetify']
        }
      ]
    };
  },
  mounted() {
    this.animateTaxi();
    this.animatePeople();
    this.animateTools();
  },
  methods: {
    animateTaxi() {
      const car = document.querySelector('#taxi-animation .car');
      let pos = 0;
      setInterval(() => {
        if (pos === 100) {
          pos = 0;
        } else {
          pos++;
          car.style.left = pos + '%';
        }
      }, 50); // Замедление анимации
    },
    animatePeople() {
      const person1 = document.querySelector('#work-animation .person1');
      const person2 = document.querySelector('#work-animation .person2');
      let pos1 = 0;
      let pos2 = 100;
      setInterval(() => {
        if (pos1 === 100) {
          pos1 = 0;
        } else {
          pos1++;
          person1.style.left = pos1 + '%';
        }
        if (pos2 === 0) {
          pos2 = 100;
        } else {
          pos2--;
          person2.style.left = pos2 + '%';
        }
      }, 50); // Замедление анимации
    },
    animateTools() {
      const tools = document.querySelectorAll('#tools-animation .tool');
      tools.forEach((tool) => {
        let pos = 0;
        setInterval(() => {
          if (pos === 100) {
            pos = 0;
          } else {
            pos++;
            tool.style.left = pos + '%';
          }
        }, 50); // Замедление анимации
      });
    }
  }
}
</script>

<style scoped>
.about {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
  background-color: #f0f0f0;
}

.project {
  background-color: white;
  border-radius: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  margin: 20px 0;
  padding: 20px;
  width: 80%;
}

.project-title {
  font-size: 1.5rem;
  color: #333;
  margin-bottom: 10px;
}

.project-description {
  font-size: 1rem;
  color: #666;
  margin-bottom: 10px;
}

.technologies {
  list-style: none;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.technologies li {
  background-color: #007bff;
  color: white;
  padding: 5px 10px;
  border-radius: 5px;
  font-size: 0.875rem;
}

.animation {
  position: relative;
  height: 100px;
  overflow: hidden;
}

.car {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  align-items: center;
}

.car-body {
  width: 80px;
  height: 40px;
  background-color: blue;
  border-radius: 5px;
}

.wheel {
  width: 20px;
  height: 20px;
  background-color: black;
  border-radius: 50%;
  position: absolute;
  bottom: -10px;
}

.wheel-front {
  left: 10px;
}

.wheel-back {
  right: 10px;
}

.person {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
}

.head {
  width: 20px;
  height: 20px;
  background-color: orange;
  border-radius: 50%;
}

.body {
  width: 20px;
  height: 40px;
  background-color: orange;
  border-radius: 5px;
}

.tool {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
}

.handle {
  width: 5px;
  height: 40px;
  background-color: brown;
}

.head {
  width: 20px;
  height: 20px;
  background-color: green;
  border-radius: 50%;
}

.person1 {
  left: 0;
}

.person2 {
  left: 100%;
}

.tool1, .tool2, .tool3 {
  top: calc(33.33% - 10px);
}

.tool2 {
  top: calc(66.66% - 10px);
}

.tool3 {
  top: calc(100% - 10px);
}
</style>
