
<template>
  <header class="header">
    <a href="/" target="_self" class="logo">
      <img src="../assets/easy-calc.svg" class="logo-img" width="150" height="59" alt="icone da easy calc">
    </a>
  </header>
</template>

<style scoped>
header {
  position: sticky;
  background: #E85B4A;
  width: 100%;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 1rem;
}

.logo{
  margin-left: 1rem;
}

nav{
  display: flex;
  align-items: center;
}

nav a {
  color: #fff;
  padding: 0.8rem;
  border-radius: 1rem;
  line-height: normal;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;

}
</style>
