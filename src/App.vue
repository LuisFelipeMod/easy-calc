<script setup lang="ts">
import Header from './components/Header.vue'
import Calculator from './components/Calculator.vue'
</script>

<template>
  <div>
    <Header msg="Easy Calc" />
    <main>
      <Calculator/>
    </main>

    <footer>
      <code>
        Desenvolvido por: <a href="https://github.com/LuisFelipeMod" target="_blank">Luis Modesto</a>
      </code>
    </footer>
  </div>
</template>

<style scoped>

  footer{
    display: flex;
    justify-content: center;
  }
</style>
