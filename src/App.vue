<template>
  <div class="container-fluid">
    <div class="converter">
<!--      Приветствие   -->
      <div class="txt-zaglv">Добро пожаловать в конвертер величин.</div>

<!--      Блоки перевода из одной величины в другую   -->
      <div class="input">
        <div class="input-block">
          Метры <br>
<!--          Остлеживаем конкретную величину и подключаем нужную функцию-->
          <input
              v-bind:value="meter"
              @input="inputMeter"
          >
        </div>
<!--        Решение не несущее функционала. Заполняет пусто пространоство. -->
        <div class="input-between-block">
          <button class="btn input-between-block-btn">&harr;</button>
        </div>
        <div class="input-block">
          Футы <br>
          <input
              v-bind:value="feet"
              @input="inputFeet"
          >
        </div>
      </div>
<!--    Далее все по аналогии   -->
      <div class="input">
        <div class="input-block">
          Морские мили <br>
          <input
              v-bind:value="nauticalMile"
              @input="inputNauticalMile"
          >
        </div>
        <div class="input-between-block">
          <button class="btn input-between-block-btn">&harr;</button>
        </div>
        <div class="input-block">
          Километры <br>
          <input
              v-bind:value="kilometr"
              @input="inputKilometr"
          >
        </div>
      </div>

      <div class="input">
        <div class="input-block">
          Градусы <br>
          <input
              v-bind:value="degrees"
              @input="inputDegrees"
          >
        </div>
        <div class="input-between-block">
          <button class="btn input-between-block-btn">&harr;</button>
        </div>
        <div class="input-block">
          Радианы <br>
          <input
              v-bind:value="radians"
              @input="inputRadians"
          >
        </div>
      </div>

      <div class="input">
        <div class="input-block">
          Температура по Цельсию <br>
          <input
              v-bind:value="celsius"
              @input="inputCelsius"
          >
        </div>
        <div class="input-between-block">
          <button class="btn input-between-block-btn">&harr;</button>
        </div>
        <div class="input-block">
          Температура по Фаренгейту <br>
          <input
              v-bind:value="fahrenheit"
              @input="inputFahrenheit"
          >
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  data() {
    // Переменные
    // Метры, футы, морские мили, километры, градусы, радианы, цельсии, фаренгейты
    return {
      meter: "",
      feet: "",
      nauticalMile: "",
      kilometr: "",
      degrees: "",
      radians: "",
      celsius: "",
      fahrenheit: "",
    }
  },
  methods: {
    // Методы для получение данных из инпутов и обновления их в переменных
    inputMeter(event) {
      this.meter = event.target.value;
      this.feet = this.meter * 3.28084;
    },
    inputFeet(event) {
      this.feet = event.target.value;
      this.meter = this.feet / 3.28084;
    },
    inputNauticalMile(event) {
      this.nauticalMile = event.target.value;
      this.kilometr = this.nauticalMile * 1.852;
    },
    inputKilometr(event) {
      this.kilometr = event.target.value;
      this.nauticalMile = this.kilometr / 1.852;
    },
    inputDegrees(event) {
      this.degrees = event.target.value;
      this.radians = this.degrees * (Math.PI) / 180;
    },
    inputRadians(event) {
      this.radians = event.target.value;
      this.degrees = this.radians / (Math.PI) * 180;
    },
    inputCelsius(event) {
      this.celsius = event.target.value;
      this.fahrenheit = (this.celsius * 9 / 5) + 32;
    },
    inputFahrenheit(event) {
      this.fahrenheit = event.target.value;
      this.celsius = (this.fahrenheit - 32) * 5 / 9;
    },
  }
}
</script>

<style>
/* Стили */
body {
  min-height: 100%;
  background-image: url("../src/assets/theme1.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: top center;
  color: #F3F7F8;
}

.txt-zaglv {
  font-size: xx-large;
  display: flex;
  justify-content: center;
}

.input-between-block-btn {
  border: none;
  text-decoration: none;
  font-size: xxx-large;
  color: #F3F7F8;
}

.input-between-block {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 1em;
  margin-top: auto;
  margin-bottom: auto;
}

.input-block {
  display: table-cell;
  vertical-align: middle;
  background-color: #D4C9E0;
  color: #293577;
  padding: 1em;
}

.converter {
  margin-top: 1em;
  margin-left: auto;
  margin-right: auto;
  width: 40%;
}

.input {
  display: flex;
  justify-content: space-between;
  margin: 2em 0em;
}
</style>
