<script lang="ts">
export default {
  data() {
    return {
      hours1: 0,
      minutes1: 0,
      seconds1: 0,
      hours2: 0,
      minutes2: 0,
      seconds2: 0,
      calculationType: 'subtract',
    };
  },
  computed: {
    result() {
      try {
        const totalSeconds1 =
          (Number(this.hours1) || 0) * 3600 + (Number(this.minutes1) || 0) * 60 + (Number(this.seconds1) || 0);
        const totalSeconds2 =
          (Number(this.hours2) || 0) * 3600 + (Number(this.minutes2) || 0) * 60 + (Number(this.seconds2) || 0);
        let resultSeconds:number;


        if (this.calculationType === 'subtract'){
          resultSeconds = totalSeconds1 - totalSeconds2;
        } else {
          resultSeconds = totalSeconds1 + totalSeconds2;
        }

        const hours = Math.floor(resultSeconds / 3600);
        const minutes = Math.floor((resultSeconds % 3600) / 60);
        const seconds = resultSeconds % 60;

        return { hours, minutes, seconds };
      } catch (error) {
        console.error('Erro no cálculo de resultados:', error);
        return { hours: 0, minutes: 0, seconds: 0 };
      }
    },
  },
  methods: {
    setCalculationType(type: string) {
      this.calculationType = type;
    },
  },
};
</script>

<template>
  <div class="calculator">
    <nav>
      <ul>
        Tipo de cálculo:
        <li :class="{active: calculationType==='subtract'}" @click="setCalculationType('subtract')">Subtrair horas</li>
        <li :class="{active: calculationType==='sum'}" @click="setCalculationType('sum')">Somar horas</li>
      </ul>
    </nav>
    <div class="calculator-box">
      <h1>{{calculationType === 'subtract' ? 'Subtrair horas' : 'Somar horas'}}</h1>
      <input type="number" v-model="hours1" maxlength="5" required /> H
      <input type="number" v-model="minutes1" maxlength="5" required /> M
      <input type="number" v-model="seconds1" maxlength="5" /> S
      <hr />
    </div>
    <div class="calculator-box">
      <input type="number" v-model="hours2" maxlength="5" required /> H
      <input type="number" v-model="minutes2" maxlength="5" required /> M
      <input type="number" v-model="seconds2" maxlength="5" /> S
      <hr />
    </div>
  </div>
  <div id="result">
    <h2>Resultado:</h2>
    <input type="number" :value="result.hours" disabled /> H
    <input type="number" :value="result.minutes" disabled /> M
    <input type="number" :value="result.seconds" disabled /> S
  </div>
</template>

<style scoped>
ul {
  list-style-type: none;
  display: flex;
  gap: 0.5rem;
  display: flex;
  align-items: center;
}

nav > ul > li {
  background: #e85b4a;
  padding: 0.3rem;
  border-radius: 0.5rem;
  cursor: pointer;
}

nav > ul > li.active {
  opacity: 0.5;
  background: #e85b4a;
}

input {
  width: 2rem;
  height: 2rem;
  padding: 1rem;
  border-radius: 1rem;
}
</style>
