<template>
  <div class="app">
    <h1>Cifrado con Código ASCII en Vue.js</h1>

    <div class="input-container">
      <label for="text">Texto a cifrar/descifrar:</label>
      <input v-model="inputText" type="text" id="text" />
    </div>

    <div class="input-container">
      <label for="shift">Valor de desplazamiento:</label>
      <input v-model.number="shift" type="number" id="shift" />
    </div>

    <div class="button-container">
      <button @click="encrypt">Cifrar</button>
      <button @click="decrypt">Descifrar</button>
    </div>

    <div class="input-container">
      <label for="result">Texto cifrado/decifrado:</label>
      <input v-model="result" type="text" id="result" readonly />
    </div>

    <h2>ALAN DE JESUS MARTINEZ HERNANDEZ <br> 7ºA  <br> INGENIERIA EN DESARROLLO Y GESTION DE SOFTWARE  </h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputText: '',
      shift: 3,
      result: '',
    };
  },
  methods: {
    encrypt() {
      this.result = this.caesarCipher(this.inputText, this.shift);
    },
    decrypt() {
      this.result = this.caesarCipher(this.inputText, -this.shift);
    },
    caesarCipher(text, shift) {
      return text
        .split('')
        .map((char) => {
          let code = char.charCodeAt(0);

          // Aplica el desplazamiento al código ASCII
          code += shift;

          return String.fromCharCode(code);
        })
        .join('');
    },
  },
};
</script>

<style scoped>
.app {
  max-width: 400px;
  margin: 0 auto;
  text-align: center;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  background-color: #f5f5f5;
}

.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 10px;
}

label {
  text-align: left;
  font-weight: bold;
  margin-bottom: 5px;
}

input[type="text"],
input[type="number"] {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #007BFF;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-right: 10px;
}

button:hover {
  background-color: #0056b3;
}

.input-container label,
.input-container input,
.button-container button,
.button-container button:hover {
  transition: 0.3s;
}


</style>
