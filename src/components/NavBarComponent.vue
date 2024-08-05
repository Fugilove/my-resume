<template>
  <nav class="navbar">
    <a href="#" @click="navigate('/')">Главная</a>
    <a href="#" @click="navigate('/about')">Что я делал</a>
    <a href="#" @click="navigate('/experience')">TODO</a>
    
    <a href="#" @click="navigate('/contact')">Как со мной связаться</a>
  </nav>
</template>

<script>
export default {
  name: 'NavBarComponent',
  methods: {
    navigate(path) {
      this.$router.push(path);
    }
  }
}
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  gap: 20px;
  background:#007bff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 10px;
}
.navbar a {
  text-decoration: none;
  color: #333;
  font-weight: bold;
  transition: color 0.3s;
}
.navbar a:hover {
  color: #007bff;
}
</style>
