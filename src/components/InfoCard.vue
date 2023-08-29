<template class="prueba">
  <div class="component-container">
    <h1 class="title-card">¿Cómo funciona?</h1>
    <div class="image-container">
      <img class="image-card" src="../assets/como_funciona.png"/>
    </div>
    <p class="description">
      Este es un servicio gratuito de <span class="name">todolegal</span>
    </p>
  </div>
</template>

<style scoped>
.component-container {
  display: flex;
  flex-direction: column;
}

.title-card {
  font-family: 'Work Sans', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  font-size: 45px;
  color: #197DFA;
  font-weight: 600;
  margin-top: 15px;
  margin-bottom: 0;
}

.image-container {
  margin-bottom: 10px;
}

.image-card {
  width: 400px;
  height: 280px;
  margin-top: 130px;
}

.description {
  font-size: 25px;
  line-height: 1.5;
  font-family: 'Martel', serif;
  color: #8E8F8F;
  margin-top: 40px;
}

.name{
    font-weight: bold;
    color: #2C89FA;
}

@media (max-width: 768px) {
  .component-container {
    display: flex;
    flex-direction: row-reverse;
    align-items: center;
    justify-content: space-around;
    padding: 0px 10px;
}
  .title-card{
  font-family: 'Work Sans', sans-serif;
  font-size: 19px;
  color: #197DFA;
  font-weight: 800;
  margin-top: 0;
  }
  .image-container {
  margin-bottom: 0;
  }
  .image-card {
  width: 120px;
  height: 90px;
  margin-top: 0;
  padding: 5px 0px;
  }
  .description{
    display: none;
  }
}
</style>
