<template>
  <NavBar />
  <div class="content-page">
    <div class="container-page">
      <div class="progress-bar">
        <IndicatorSection
          class=""
          :sections="sections"
          :activeIndex="activeIndex"
        />
      </div>
      <div class="container-cards">
        <div class="component-left">
          <InfoCard class="info info-card" />
        </div>
        <div class="component-right">
          <DocumentUpload @files="files = $event" class="upload-files info-card" />
          <div class="container-button">
            <ButtonNext :files="files"/>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import DocumentUpload from "./components/DocumentUpload.vue";
import ButtonNext from "./components/ButtonNext.vue";
import NavBar from "./components/NavBar.vue";
import InfoCard from "./components/InfoCard.vue";
import IndicatorSection from "./components/IndicatorSection.vue";

export default {
  name: "App",
  data() {
    return {
      // apiUrl: "https://webhook.site/04b12921-3072-4fe9-8d60-9f4394e109d9",
      apiUrl: "https://webhook.site/a969781c-7074-40fb-9f17-bdb5ba64c3e3",
      sections: [
        { title: "Cargar documento" },
        { title: "Indicar firmantes" },
        { title: "Personalizaciones Opcionales" },
      ],
      activeIndex: 0,
      files: [],
    };
  },
  components: {
    DocumentUpload,
    ButtonNext,
    NavBar,
    InfoCard,
    IndicatorSection,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  padding: 0;
}

body {
  margin: 0;
  /* height: 100vh; */
}

.content-page {
  background: -webkit-linear-gradient(to top, #eef2f3, #8e9eab);
  background: linear-gradient(to top, #d9e2f2, #f5f6f6);
  height: 93.2vh;
  display: flex;
  width: 100%;
  flex-direction: row;
  justify-content: center;
}

.progress-bar {
  margin: auto;
  margin-top: 25px;
  border-radius: 20px;
  background-color: white;
  border-radius: 20px;
  width: 100%;
}

.container-page {
  width: 80%;
}

.container-cards {
  display: flex;
  justify-content: space-around;
  flex-direction: row;
  align-items: center;
  width: 100%;
  margin-top: 3%;
}

.component-left {
  padding: 10px;
  background-color: white;
  border-radius: 20px;
  width: 49%;
  margin-right: 2%;
  height: 600px;
}

.component-right {
  padding: 10px;
  background-color: white;
  position: relative;
  border-radius: 20px;
  width: 49%;
  margin-left: 2%;
  min-height: 600px;
}

.info-card {
  box-sizing: border-box;
}

.container-button {
  display: flex;
  flex-direction: column;
  align-items: center;
  /* margin-top: 120px; */
}

.navbar {
  background-color: white;
  position: relative;
  top: 0;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

@media (max-width: 768px) {
  #app{
  width: 100%;
  /* background: -webkit-linear-gradient(to top, #eef2f3, #8e9eab);
  background: linear-gradient(to top, #d9e2f2, #f5f6f6); */
  }

  .navbar{
    padding: 20px 0px;
    background-color: #f5f6f6;
  }
  .container-page{
    width: 100%;
  }
  .container-cards {
    display: flex;
    flex-direction: column;
  }

  .component-left{
    width: 350px;
    margin: 0px 40px;
    height: 100px;
  }

  .component-right {
    margin-top: 30px;
    width: 350px;
    margin-right: 40px;
    margin-left: 40px;
    min-height: 20px;
  }

  .progress-bar {
    display: none;
  }
 
}
</style>
