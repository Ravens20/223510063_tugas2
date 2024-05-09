<template>
  <div class="container" :style="{ backgroundColor: backgroundColor }">
    <h1 :class="{ blue: isBlue, red: isRed }">{{ title }}</h1>
    <p>{{ inputText }}</p>
    
    <input type="text" v-model="inputText" @input="changeText" placeholder="Ketik sesuatu..." class="input-field">
    
    <button :style="{ backgroundColor: buttonColor }" @click="changeColor" class="color-button">Ubah Warna</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isBlue: false,
      isRed: false,
      inputText: '',
      title: 'Dindra Desvantio',
      buttonColors: ['#FF5733', '#33FF57', '#5733FF', '#33FFFF'],
      backgroundColors: ['#F0F0F0', '#F5F5F5', '#FAFAFA', '#E0E0E0'],
      buttonIndex: 0,
      backgroundIndex: 0
    };
  },
  computed: {
    buttonColor() {
      return this.buttonColors[this.buttonIndex];
    },
    backgroundColor() {
      return this.backgroundColors[this.backgroundIndex];
    }
  },
  methods: {
    changeColor() {
      this.isBlue = !this.isBlue;
      this.isRed = !this.isRed;
      
      
      this.buttonIndex = (this.buttonIndex + 1) % this.buttonColors.length;
      this.backgroundIndex = (this.backgroundIndex + 1) % this.backgroundColors.length;
    },
    changeText(event) {
      this.inputText = event.target.value;
    }
  }
};
</script>

<style>
.container {
  max-width: 600px;
  margin: auto;
  text-align: center;
  padding: 20px;
  border-radius: 10px;
  transition: background-color 0.5s ease;
  color: blue;
  position: relative;
  left: 200px;
}

h1 {
  font-size: 2.5rem;
  transition: color 0.3s ease;
}

p {
  font-size: 1.2rem;
  margin-bottom: 20px;
}

.input-field, .color-button {
  font-size: 1rem;
  padding: 10px;
  margin: 5px;
  border: 2px solid #333;
  border-radius: 5px;
  transition: all 0.3s ease;
  width: 80%;
}

input:focus, button:focus {
  outline: none;
}

button {
  cursor: pointer;
  color: #fff;
}

.blue {
  color: blue;
}

.red {
  color: red;
}
</style>
