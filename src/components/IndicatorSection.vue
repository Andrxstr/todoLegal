<template>
    <div class="section-indicator">
        <h3 class="title_signature"><b>Firmar nuevo documento</b></h3>
      <div
        v-for="(section, index) in sections"
        :key="index"
        class="section"
        :class="{ active: index === activeIndex }"
      >
        <div class="content">
          <div class="circle" :class="{ active: index === activeIndex }">{{ index + 1 }}</div>
          <div class="info">
            <div class="title" :class="{ active: index === activeIndex }">{{ section.title }}</div>
          </div>
        </div>
      </div>
    </div>
  </template>

<script>
export default {
  props: {
    sections: Array, 
    activeIndex: Number, 
  },
};
</script>

<style scoped>
.section-indicator {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  background-color: white;
  border-radius: 20px;
}

.title_signature{
    color: #002179;
    /* margin-left: 40px; */
    font-family: 'Noto Sans Symbols', sans-serif;
}

.section {
  display: flex;
  align-items: center;
}

.content {
  display: flex;
  align-items: center;
  /* background-color: white; */

}

.circle {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: white;
  border: 2px solid #3A77EC;
  color: #3A77EC;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: bold;
  margin-right: 10px;
}

.circle.active {
  background-color: #3A77EC;
  border: 2px solid #3A77EC;
  color: white;
}

.info {
  display: flex;
  flex-direction: column;
  
}

.title {
  color: #8B8AB8; 
  margin-right: 10px;
  
}

.title.active {
  color: #3D79EC;
  background-color: white;
  margin: 10px;

}

</style>