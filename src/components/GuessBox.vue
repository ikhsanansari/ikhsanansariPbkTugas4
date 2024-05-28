<template>
    <div
      class="guess-box"
      :class="{ correct: isCorrect, wrong: isWrong }"
      :style="{ backgroundColor: bgColor }"
    >
      <h2>Tebak Angka</h2>
      <slot name="info"></slot>
      <guess-input @checkGuess="checkGuess"></guess-input>
    </div>
  </template>
  
  <script>
  import GuessInput from './GuessInput.vue';
  
  export default {
    components: {
      GuessInput
    },
    data() {
      return {
        isCorrect: false,
        isWrong: false,
        bgColor: 'white',
      };
    },
    methods: {
      checkGuess(userGuess) {
        const randomNumber = Math.floor(Math.random() * 200); // Generate angka acak antara 0 dan 200
        let resultMessage;
        if (userGuess === null || isNaN(userGuess)) {
          resultMessage = 'Masukkan tebakan yang valid!';
          this.bgColor = '#e74c3c'; // Merah
        } else if (userGuess == randomNumber) {
          this.isCorrect = true;
          resultMessage = `Tebakan Anda benar! Angka yang benar adalah ${randomNumber}.`;
          this.bgColor = '#2ecc71'; // Hijau
        } else {
          this.isWrong = true;
          resultMessage = `Tebakan Anda salah! Angka yang benar adalah ${randomNumber}.`;
          this.bgColor = '#e74c3c'; // Merah
        }
        this.$emit('guessResult', resultMessage);
      }
    }
  };
  </script>
  
  <style>
  .guess-box {
    border-radius: 10px;
    padding: 20px;
    text-align: center;
    border: 2px solid #3498db;
  }
  .correct {
    border-color: #2ecc71; /* Hijau */
  }
  .wrong {
    border-color: #e89389; /* Merah */
  }
  </style>
  