<template>
  <div class="center">
    <div class="clock">
      <table>
        <tr>
          <td style="width: 119px"><div class="text">{{hours}}</div></td>
          <td style="width: 20px"><div>:</div></td>
          <td style="width: 119px"><div class="text">{{minutes}}</div></td>
          <td style="width: 20px"><div>:</div></td>
          <td style="width: 119px"><div class="text">{{seconds}}</div></td>
        </tr>
      </table>
    </div>
    <div class="buttons">
      <button @click="this.start()">Start</button>
      <button @click="this.stop()">Stop</button>
      <button @click="this.reset()">Reset</button>
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
      startbool: false,
      hours: '00',
      minutes: '00',
      seconds: '00',
    };
  },
  methods: {
    start() {
      if(this.startbool){
        return;
      }
      this.startbool = true;
      this.interval = setInterval(() => {
        this.time++;
        this.hours = Math.floor(this.time / 3600);
        this.minutes = Math.floor((this.time % 3600) / 60);
        this.seconds = this.time % 60;
        if (this.hours < 10) {
          this.hours = '0' + this.hours;
        }
        if (this.minutes < 10) {
          this.minutes = '0' + this.minutes;
        }
        if (this.seconds < 10) {
          this.seconds = '0' + this.seconds;
        }
      }, 1000);
    },
    stop() {
      this.startbool = false;
      clearInterval(this.interval);
    },
    reset() {
      this.startbool = false;
      this.time = 0;
      this.hours = '00';
      this.minutes = '00';
      this.seconds = '00';
      this.stop();
    },
  },
}
</script>

<style scoped>
@font-face {
  font-family: silkscreen;
  src: url("../../../silkscreen/FrostbiteBossFight-dL0Z.ttf");
}
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
  width: 30%;
  height: 30%;
}
.clock{
  font-family: silkscreen;
  font-size: 800%;
  font-weight: bold;
  margin-bottom: 10%;
  color: #E2DFF5;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: row;
}

.buttons{
  display: flex;
  justify-content: space-around;
  width: 100%;
}
button{
  margin-top: 3%;
  width: 17%;
  height: 110%;
  background-color: rgba(76, 62, 82, 0.5);
  border: none;
  border-radius: 10px;
  color: #E2DFF5;
  font-family: silkscreen;
  font-size: 115%;
}
button:hover{
  background-color: #312835;
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(125, 111, 192, 0.6);
  border: rgba(241, 241, 241, 0.13);
}
table{
  justify-content: center;
  align-items: center;
  flex-direction: row;
  width: 50px;
  table-layout: fixed;
}
table td{
  box-sizing: border-box;
  text-align: center;
  overflow: hidden;
  text-overflow: ellipsis;
}
@media (max-width: 1000px) {
  .center {
    padding: 0;
    width: 90%;
    height: 20%;
  }
  .clock{
    font-size: 750%;
  }
  button{
    width: 20%;
    height: 200%;
  }
}
</style>
