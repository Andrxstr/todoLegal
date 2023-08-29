<template>
  <div class="buttons">
    <div v-if="files.length > 0">
    <div class="button-back">Regresar</div>
    <div class="button-next" @click="enviarInformacion">Siguiente</div>
  </div>
  <div v-else>
    <div class="button-next-only" @click="enviarInformacion">Siguiente</div>
  </div>
  </div>
</template>

<script>
import axios from "axios";
import ApiCaller from "../App.vue";
export default {
  name: "ButtonNext",
  props: {
    files: {type: Array, required: true}
  },
  data() {
    return {
      nombre: "Andres", 
      horaLocal: new Date().toLocaleString(),
      direccionIP: "192.168.0.1", 
    };
  },
  methods: {
    enviarInformacion() {
      const datos = {
        nombre: this.nombre,
        horaLocal: this.horaLocal,
        direccionIP: this.direccionIP,
      };

      axios
        .post(ApiCaller.data().apiUrl, datos)
        .then((response) => {
          console.log("Respuesta :", response.config.data);
        })
        .catch((error) => {
          console.error("Error al enviar los datos:", error);
        });
    },
  },
};
</script>

<style scoped>

.button-next {
  background-color: #3b77ed;
  width: 33%;
  padding: 20px;
  color: white;
  border-radius: 10px;
  position: absolute;
  bottom: 35px;
  cursor: pointer;
  right: 200px;
  /* margin-right: 500px; */
}
.button-next-only {
  background-color: #3b77ed;
  width: 33%;
  padding: 20px;
  color: white;
  border-radius: 10px;
  position: absolute;
  bottom: 35px;
  cursor: pointer;
  right: 200px;
  /* margin-right: 500px; */
}

.button-back {
  display: none;
}

@media (max-width: 768px) {
  .buttons{
    display: flex;
  }
  .button-next {
    display: block;
    position: fixed;
    bottom: 0;
    left: 196px;
    width: 50%;
    height: 45px;
    padding: 10px 0;
    background-color: #3b77ed;
    color: white;
    text-align: center;
    border-radius: 0;
    font-size: 20px;
    font-family: "Martel", serif;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .button-back {
    display: block;
    position: fixed;
    bottom: 0;
    left: 0;
    width: 50%;
    height: 41px;
    padding: 10px 0;
    background-color: white;
    color: #3b77ed;
    border: 2px solid #3b77ed;
    text-align: center;
    border-radius: 0;
    font-size: 20px;
    font-family: "Martel", serif;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .button-next-only {
    display: block;
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 45px;
    padding: 10px 0;
    background-color: #3b77ed;
    color: white;
    text-align: center;
    border-radius: 0;
    font-size: 20px;
    font-family: "Martel", serif;
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>
