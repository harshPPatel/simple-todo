<template>
  <header>
    <h1>Your To-Do</h1>
    <p>A Basic To-Do Task Manager only for You!</p>
  </header>
</template>

<style lang="scss" scoped>
  header {
    text-align: center;
    margin-bottom: 60px;

    @media (max-width: 375px) {
      margin-bottom: 30px;
    }
    h1 {
      font-family: "Aladin", Arial, Helvetica, sans-serif;
      font-size: 85px;
      letter-spacing: 4px;
      color: #2E2E2E;
      text-shadow: 0 5px 0 rgba(black, 0.1);
      margin-bottom: 10px;

      @media (max-width: 550px) {
        font-size: 64px;
      }
      @media (max-width: 375px) {
        font-size: 52px;
        margin-bottom: 0px;
      }
    }
    p {
      color: #FF7350;
      @media (max-width: 550px) {
        width: 90%;
        margin: 0 auto;
      }
    }
  }
</style>
