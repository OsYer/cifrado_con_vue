<template>
  <div id="app">
    <div class="container">
      <textarea v-model="data" rows="4" cols="50" class="textarea"></textarea>
      <button @click="encryptData" class="btn">Cifrar</button>
      <button @click="decryptData" class="btn">Descifrar</button>
      <div class="result-container">
        <p class="result"> {{ result }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import CryptoJS from "crypto-js";

export default {
  name: 'App',
  data() {
    return {
      key: "my-secret-key",
      data: "",
      result: "", // Única variable para mostrar el resultado
    };
  },
  methods: {
    encryptData() {
      const cipher = CryptoJS.AES.encrypt(this.data, this.key).toString();
      this.result = `${cipher}`;
    },
    decryptData() {
      const decipher = CryptoJS.AES.decrypt(this.data, this.key).toString(CryptoJS.enc.Utf8);
      this.result = ` ${decipher}`;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #f0f0f0;
}

.container {
  text-align: center;
  background-color: #fff;
  border-radius: 5px;
width: 50%;
  padding: 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

.textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.btn {
  margin: 10px;
  padding: 10px 20px;
  background-color: #007BFF;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.2s;
}

.btn:hover {
  background-color: #0056b3;
}

.result-container {
  height: 60px; /* Altura fija para el contenedor del resultado */
  align-items: center;
  justify-content: center;
  overflow: auto; /* Agregar desbordamiento para el resultado */
}

.result {
  font-weight: bold;
}
</style>
