<template>
  <div class="container">
    <!-- Teks Hello everyone berada di paling atas dan ditengah dengan latar belakang -->
    <h1 class="header">Hello everyone</h1>

    <!-- Elemen input teks -->
    <div class="input-group">
      <input v-model="inputText" placeholder="Masukkan teks di sini" class="text-input" />

      <!-- Dropdown untuk memilih warna -->
      <select v-model="selectedColor" class="color-select">
        <option value="black">Default (Hitam)</option>
        <option value="red">Merah</option>
        <option value="blue">Biru</option>
        <option value="green">Hijau</option>
      </select>
    </div>

    <!-- Penggunaan class bindings dan style bindings -->
    <div :style="{ color: selectedColor }" class="dynamic-text">
      {{ inputText }}
    </div>

    <!-- Interaksi dinamis dengan event listener -->
    <div class="button-group">
      <button @click="changeText" class="btn">Change Text to default</button>
      <button @click="sayHi" class="btn">Click</button> <!-- Tombol dipindahkan ke bawah -->
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputText: '',
      dynamicText: 'Teks ini akan berubah!',
      selectedColor: 'black',
      colorMappings: {
        merah: 'red',
        biru: 'blue',
        hijau: 'green'
      }
    };
  },
  methods: {
    changeText() {
      if (this.inputText.toLowerCase() in this.colorMappings) {
        // Jika warna yang dimasukkan pengguna ada dalam mapping, gunakan warna tersebut
        this.selectedColor = this.colorMappings[this.inputText.toLowerCase()];
        this.dynamicText = `Teks telah diubah menjadi ${this.inputText.toLowerCase()}`;
      } else {
        // Jika tidak, kembalikan ke warna default
        this.selectedColor = 'black';
        this.dynamicText = 'Teks ini akan berubah!';
      }
    },
    sayHi() {
      alert("Hello, how are you doing today?");
      this.dynamicText = "Hi, selamat datang!";
    },
  },
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: linear-gradient(to bottom, #d3d3d3, #a9a9a9);
  padding: 50px;
  border-radius: 15px;
}

.header {
  text-align: center;
  margin-bottom: 40px;
  font-size: 2em;
  color: #333;
}

.input-group {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-bottom: 30px;
}

.text-input, .color-select {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.dynamic-text {
  text-align: center;
  font-size: 1.5em;
  margin-bottom: 20px;
}

.button-group {
  display: flex;
  gap: 20px;
}

.btn {
  padding: 10px 20px;
  border: none;
  background-color: #007bff;
  color: white;
  border-radius: 5px;
  cursor: pointer;
}

.btn:hover {
  background-color: #0056b3;
}
</style>
