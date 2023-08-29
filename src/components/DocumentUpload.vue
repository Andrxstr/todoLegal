<template>
  <div class="document-uploader">
    <h3 class="title-documents">Carga de Documentos</h3>
    <p class="indication">
      Sube tus documentos y ordénalos
      <button class="info-button">
        <span class="info-icon">?</span>
      </button>
    </p>
    <div
      v-if="files.length == 0"
      class="drop-area"
      @dragover.prevent
      @drop="handleDrop"
    >
      <label for="file-input"><img class="img-upload-files" src="../assets/subir_documento.png" /></label>
      <p class="text-upload">
        Arrastra y suelta tus documentos aquí o
        <label for="file-input" class="file-label">Buscar archivo</label>
      </p>
      <input
        type="file"
        id="file-input"
        ref="fileInput"
        class="file-inputs"
        accept=".pdf"
        @change="handleFileChange"
      />
    </div>
    <div v-else class="drop-area-docs" @dragover.prevent @drop="handleDrop">
      <img class="image-upload-files" src="../assets/subir_documento.png" />
      <div v-for="file in files" :key="file.url" class="show-document">
        <a class="icons-files" :href="file.url" target="_blank"
          ><img src="../assets/seleccion.png"
        /></a>
        <p class="vertical-line"></p>
        <a class="file-name">{{
          limitCharacters(file.name.replace(".pdf", ""), 10)
        }}</a>
        <p class="vertical-line"></p>
        <img
          class="icons-delete"
          @click="deleteFile(file)"
          src="../assets/papelera.png"
        />
      </div>

      <div v-if="files.length < maxItems" class="add-document">
        <label for="file-input" class="icons-files"
          ><img src="../assets/añadir.png"
        /></label>
        <input
          type="file"
          id="file-input"
          ref="fileInput"
          class="file-inputs"
          accept=".pdf"
          @change="handleFileChange"
        />
        <p class="vertical-line"></p>
        <a class="file-add">Añadir más documentos</a>
        <p class="vertical-line"></p>
        <p class="document-indications">5 Máx 20 Mb</p>
      </div>
    </div>
    <div v-if="errorMessage" class="error">{{ errorMessage }}</div>
  </div>
</template>

<script>
export default {
  name: "DocumentUpload",
  data() {
    return {
      selectedFile: null,
      files: [],
      errorMessage: null,
      maxSize: 20 * 1024 * 1024,
      maxItems: 5,
    };
  },
  methods: {
    handleDrop(event) {
      event.preventDefault();
      const file = event.dataTransfer.files[0];
      this.errorMessage = this.validate(file)
      if(this.errorMessage) return
          let selectedFile = {
            name: file.name,
            url: URL.createObjectURL(file),
          };
          this.files.push(selectedFile);
          this.$emit('files', this.files);
          this.errorMessage = null;
    },
    handleFileChange(event) {
      const file = event.target.files[0];
      this.errorMessage = this.validate(file)
      if(this.errorMessage) return
          let selectedFile = {
            name: file.name,
            url: URL.createObjectURL(file),
          };
          this.files.push(selectedFile);
          this.$emit('files', this.files);
          this.errorMessage = null;
    },
    deleteFile(item) {
      let index = this.files.indexOf(item);
      this.files.splice(index, 1);
      this.errorMessage = null;
    },
    limitCharacters(text, limit) {
      if (text.length > limit) {
        return text.substring(0, limit) + "...";
      }
      return text;
    },
    validate(item){
      console.log(this.files)
      if(this.files.length > this.maxItems) return 'Capacidad Maxima de Archivos Alcanzada';
      if(item && item.type !== "application/pdf") return 'Solo se admiten archivos en formato PDF';
      if(item.size > this.maxSize)return 'El archivo excede el tamaño máximo permitido (20 MB).';
      return ''
    }
  },
};
</script>

<style scoped>
.title-documents {
  font-family: "Work Sans", sans-serif;
  font-size: 25px;
  color: #002179;
  text-align: left;
  margin-left: 15px;
  margin-bottom: 0;
}
.indication {
  font-family: "Work Sans", sans-serif;
  font-weight: 500;
  text-align: left;
  margin-left: 15px;
  font-size: 20px;
  margin-top: 5px;
}

.drop-area {
  background-color: #f4f6fc;
  border: 5px dashed #7995e3;
  border-spacing: inherit;
  border-radius: 20px;
  margin: auto;
  width: 450px;
  min-height: 160px;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 25px 0px;
  justify-content: space-between;
}

.drop-area-docs {
  background-color: #f4f6fc;
  border: 5px dashed #7995e3;
  border-spacing: inherit;
  border-radius: 20px;
  margin: auto;
  width: 450px;
  min-height: 160px;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 25px 0px;
  justify-content: space-between;
}
.uploaded-document {
  margin-top: 20px;
}
.error {
  color: red;
  margin-top: 15px;
}

.info-button {
  background-color: #3a77ec;
  border: none;
  color: white;
  width: 21px;
  height: 20px;
  border-radius: 50%;
  cursor: pointer;
  text-align: center;
}

.info-icon {
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 15px;
  font-weight: 600;
}
.file-label {
  text-decoration: underline;
  cursor: pointer;
  color: #184ad1;
}

.text-upload {
  font-family: "Work Sans", sans-serif;
  font-size: 14px;
  width: 100%;
}

.file-inputs {
  display: none;
}
.show-document {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  background-color: white;
  border-radius: 12px;
  width: 380px;
  margin-bottom: 8px;
}
.icons-files {
  margin: 0 5px;
  width: 15%;
  cursor: pointer;
}

.icons-delete {
  margin: 0 20px;
  width: 8%;
}

.file-name {
  color: #a4a5a4;
  width: 80%;
  text-align: left;
  padding: 10px;
}
.file-add {
  color: #197dfa;
  width: 80%;
  text-align: left;
  padding: 10px;
}

.add-document {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  background-color: #f4f6fc;
  border: 2px solid white;
  border-radius: 12px;
  width: 380px;
}

.document-indications {
  font-size: 12px;
  font-weight: 800;
  color: #197dfa;
  padding: 4px;
  margin: 0;
  width: 20%;
}
.vertical-line {
  width: 1px;
  height: 25px; 
  background-color: #ccc; 
  margin: 0px; 
}

.image-upload-files{
  display: none;
}

@media (max-width: 768px) {
  .title-documents{
    font-size: 18px;
    margin-top: 13px;
    margin-left: 10px;
    font-weight: 800;
  }
  .indication{
    margin-left: 10px;
    font-size: 15px;
  }
  
  .text-upload{
    display: none;
  }
  .drop-area {
  background-color: #f4f6fc;
  border: 5px dashed #7995e3;
  border-radius: 20px;
  width: 200px;
  min-height: 100px;
  margin-top: 25px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 25px 0px;
  justify-content: space-between;
}


.drop-area-docs {
  background-color: #f4f6fc;
  border: 5px dashed #7995e3;
  border-spacing: inherit;
  border-radius: 20px;
  margin: auto;
  width: 320px;
  min-height: 120px;
  margin-top: 25px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 25px 0px;
  justify-content: space-between;
}

.show-document {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  background-color: white;
  border-radius: 12px;
  width: 300px;
  margin-bottom: 8px;
}

.add-document {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  background-color: #f4f6fc;
  border: 2px solid white;
  border-radius: 12px;
  width: 300px;
}

.image-upload-files{
  display: block;
}

}
</style>
