<template>
  <div class="app">
    <h1>Форма регистрации</h1>

    <!-- Поля ввода с v-model -->
    <div class="form-group">
      <label for="name">Имя:</label>
      <input 
        id="name"
        v-model="name" 
        type="text" 
        placeholder="Введите ваше имя" 
      />
    </div>

    <div class="form-group">
      <label for="email">Email:</label>
      <input 
        id="email"
        v-model="email" 
        type="email" 
        placeholder="Введите ваш email" 
      />
    </div>

    <!-- Кнопка показа данных -->
    <button @click="showData" class="btn">
      Показать данные в консоли
    </button>

    <!-- Флажок (checkbox) -->
    <div class="form-group">
      <label class="checkbox-label">
        <input type="checkbox" v-model="showMessage" />
        Показать приветственное сообщение
      </label>
    </div>

    <!-- Условное сообщение -->
    <p v-if="showMessage" class="welcome">
      Добро пожаловать, {{ name || 'гость' }}!
    </p>

    <!-- Радиокнопки -->
    <h3>Любимый язык программирования:</h3>
    <div class="radio-group">
      <label>
        <input type="radio" value="JavaScript" v-model="favoriteLang" />
        JavaScript
      </label>
      <label>
        <input type="radio" value="Python" v-model="favoriteLang" />
        Python
      </label>
      <label>
        <input type="radio" value="Java" v-model="favoriteLang" />
        Java
      </label>
    </div>

    <!-- Вывод выбранного языка -->
    <p class="result">
      Вы выбрали: <strong>{{ favoriteLang }}</strong>
    </p>

    <!-- Отладка (можно убрать) -->
    <div class="debug">
      <h4>Текущие значения:</h4>
      <p>Имя: {{ name }}</p>
      <p>Email: {{ email }}</p>
      <p>Сообщение: {{ showMessage ? 'Показано' : 'Скрыто' }}</p>
      <p>Язык: {{ favoriteLang }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

// Реактивные переменные
const name = ref('')
const email = ref('')
const showMessage = ref(false)
const favoriteLang = ref('JavaScript')

// Метод для вывода данных в консоль
const showData = () => {
  console.log('=== Данные формы ===')
  console.log('Имя:', name.value)
  console.log('Email:', email.value)
  console.log('Сообщение показано:', showMessage.value)
  console.log('Любимый язык:', favoriteLang.value)
  console.log('===================')
}

// Отслеживание изменений (дополнительно)
watch(name, (newName) => {
  console.log('Имя изменилось на:', newName)
})

watch(favoriteLang, (newLang) => {
  console.log('Выбран язык:', newLang)
})
</script>

<style scoped>
.app {
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  color: #2c3e50;
  text-align: center;
  margin-bottom: 30px;
}

.form-group {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
  color: #333;
}

.checkbox-label {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-weight: normal;
  cursor: pointer;
}

input[type="text"],
input[type="email"] {
  width: 100%;
  padding: 10px;
  border: 2px solid #ddd;
  border-radius: 6px;
  font-size: 16px;
  transition: border-color 0.3s;
  box-sizing: border-box;
}

input[type="text"]:focus,
input[type="email"]:focus {
  outline: none;
  border-color: #42b883;
}

.btn {
  display: block;
  width: 100%;
  padding: 12px;
  background-color: #42b883;
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 16px;
  cursor: pointer;
  margin: 20px 0;
  transition: background-color 0.3s;
}

.btn:hover {
  background-color: #35495e;
}

.btn:active {
  transform: scale(0.98);
}

.welcome {
  padding: 15px;
  background-color: #e8f5e9;
  border-left: 4px solid #42b883;
  border-radius: 4px;
  color: #2e7d32;
  font-size: 18px;
}

h3 {
  color: #2c3e50;
  margin: 30px 0 15px;
}

.radio-group {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 20px;
}

.radio-group label {
  display: flex;
  align-items: center;
  gap: 8px;
  font-weight: normal;
  cursor: pointer;
  padding: 8px;
  border-radius: 4px;
  transition: background-color 0.2s;
}

.radio-group label:hover {
  background-color: #f0f0f0;
}

.result {
  font-size: 18px;
  color: #2c3e50;
  padding: 10px;
  background-color: #f8f9fa;
  border-radius: 6px;
}

.result strong {
  color: #42b883;
}

.debug {
  margin-top: 30px;
  padding: 15px;
  background-color: #f8f9fa;
  border: 1px solid #ddd;
  border-radius: 6px;
  font-size: 14px;
}

.debug h4 {
  margin-top: 0;
  color: #666;
}
</style>