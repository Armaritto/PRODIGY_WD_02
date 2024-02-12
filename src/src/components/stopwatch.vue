<template>
  <div class="center">
    <div class="clock">23:59:59</div>
    <div class="buttons">
      <button>Start</button>
      <button>Stop</button>
      <button>Reset</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'stopwatch',
  data() {
    return {
      time: 0,
      interval: null,
    };
  },
}
</script>

<style scoped>
.center {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  position: absolute;
  top: 50%;
  left: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  border-radius: 30px;
  backdrop-filter: blur(5px);
  border: 2px solid  rgba(44, 19, 66, 0.13);
  box-shadow: 0 0 40px rgba(8,7,16,0.6);
  padding: 6%;
  width: 25%;
  height: 25%;
}
.clock{
  font-size: 800%;
  font-weight: bold;
  margin-bottom: 10%;
  color: #E2DFF5;
}
.buttons{
  display: flex;
  justify-content: space-around;
  width: 100%;
}
button{
  margin-top: 3%;

}
button:hover{
  background-color: #4CAF50;
  color: white;
}
</style>
