<template>
  <div id="app">
    <img src="./assets/cronometro.png" class="img">
    <a class="timer">00:00,00</a>

    <div class="areaBtn">
      <button class="botao">VAI</button>
      <button class="botao">LIMPAR</button>

    </div>
  </div>
</template>

<script>

export default {
  name: 'App',

}
</script>

<style>
#app {
  display: flex;
  width: 100%;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.img {
  width: 420px;
  height: 420px;
  padding-top: 100px;
}

.timer{
  color: #fff;
  font-size: 70px;
  margin-top: -210px;
}
.areaBtn{
  margin-top: 155px;
  display: flex;
}
.botao{
  width: 150px;
  background-color: #fff;
  font-size: 20px;
  border:0;
  border-radius: 5px;
  text-align: center;
  margin-left: 15px;
  margin-right: 15px;
  padding: 6px;
  cursor: pointer;
}
.botao:hover{
  opacity: 0.8;
  transition: all 0.50;
}
</style>
