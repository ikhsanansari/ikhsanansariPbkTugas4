<template>
  <div id="app">
    <div class="container">
      <guess-box @guessResult="handleGuessResult">
        <template v-slot:info>
          <p>Ini adalah permainan tebak angka. Masukkan tebakan Anda antara 0 dan 200.</p>
        </template>
      </guess-box>
      <p v-if="resultMessage" class="result">{{ resultMessage }}</p>
    </div>
  </div>
</template>

<script>
import GuessBox from './components/GuessBox.vue';

export default {
  components: {
    GuessBox
  },
  data() {
    return {
      resultMessage: ''
    };
  },
  methods: {
    handleGuessResult(message) {
      this.resultMessage = message;
    }
  }
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.result {
  margin-top: 20px;
  font-weight: bold;
}
</style>
