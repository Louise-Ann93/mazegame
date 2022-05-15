<template>

<div class="wrapper" @mousemove="getMouseCoord">

<div id="background-image" class="background-image"></div>

  <div id="map" class="map">
      
      <div @mouseover="mouseWarning" 
      class="wall border-top border-left">
      </div>
      <div @mouseover="mouseWarning" 
      class="wall border-top">
      </div>
      <div @mouseover="mouseWarning" 
      class="wall border-top">
      </div>

      <div class="floor border-left border-right"></div>
      
      <div @mouseover="mouseWarning" 
      class="wall border-top">
      </div>
      <div @mouseover="mouseWarning" 
      class="wall border-top border-right">
      </div>
      <div @mouseover="mouseWarning" 
      class="wall border-left">
      </div>
      <div @mouseover="mouseWarning" 
      class="wall">
      </div>

      <div class="floor border-top border-left"></div>
      <div class="floor border-bottom"></div>
      <div class="floor border-top border-right"></div>

      <div @mouseover="mouseWarning" 
      class="wall border-right">
      </div>
      <div @mouseover="mouseWarning" 
      class="wall border-left">
      </div>

      <div class="floor border-top border-left"></div>
      <div class="floor border-bottom border-right"></div>
      
      <div @mouseover="mouseWarning"
      class="wall">
      </div>

      <div class="floor border-left"></div>
      <div class="floor border-top border-bottom"></div>

      <div @mouseover="mouseWarning"  
      class="wall border-left">
      </div>

      <div class="floor border-left border-right"></div>

      <div @mouseover="mouseWarning" 
      class="wall">
      </div>
      <div @mouseover="mouseWarning" 
      class="wall">
      </div>

      <div class="floor border-left border-right"></div>

      <div @mouseover="mouseWarning"
      class="wall border-right">
      </div>
      <div @mouseover="mouseWarning"
      class="wall border-left">
      </div>

      <div class="floor border-left border-right"></div>

      <div @mouseover="mouseWarning"
      class="wall">
      </div>

      <div class="floor border-left border-top"></div>
      <div class="floor border-bottom"></div>
      <div class="floor border-top border-bottom"></div>
     
     <div @mouseover="mouseWarning"
      class="wall border-left border-bottom">
      </div>

      <div id="start" class="text floor border-left border-right">
        Start
      </div>

      <div @mouseover="mouseWarning"
      class="wall border-bottom">
      </div>

      <div id="stop" 
      @mouseover="wellDone" 
      class="text floor border-left border-right">
        Finish
      </div>
     
     <div @mouseover="mouseWarning"
      class="wall border-bottom">
      </div>
      <div @mouseover="mouseWarning"
      class="wall border-bottom border-right">
      </div>

    
<!-- <div id="clock" class="clock">
  <div class="time">{{ time }}</div>
  </div> -->

</div>

<div class="clock">Move over Start to start the timer, once you have reached the finish the timer will stop 👏🏻</div>

</div>

</template>

<script>

export default {
    name: "MazeGame",
    data() {
        return {
            warning: 0,
            pointerX: 0,
            pointerY: 0,
            time: '00:00:00.000',
            started: false,
            stopped: false,
            running: false
        };
    },
    watch: {
      warning () {
       if(this.warning == 3) {
         alert('Absolute Fail! 🙄')
         this.warning = 0
       }
      },
      pointerX () {
        if (this.pointerX == -1145) {
          document.getElementById('map').style.display = "none"
          document.getElementById("background-image").style.display = "block";
        }
      }
    },
    methods: {
        getMouseCoord(event) {
            this.pointerX = event.screenX;
            this.pointerY = event.screenY;
            console.log(this.pointerX)
        },
        mouseWarning() {
            this.warning++;
            console.log(this.warning)
        },
        wellDone () {
          alert('CONGRATS YOU WON 🎉')
        },

    },
}

</script>

<style scoped>

.wrapper {
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  min-height: 100vh;
}
.map {
text-align: center;
display: grid;
grid-template: repeat(6, 50px) / repeat(6, 50px);
}

.wall {
  background-color: green;
  cursor:url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'  width='22' height='26' viewport='0 0 100 100' style='fill:black;font-size:13px;'><text y='50%'>💩</text></svg>") 16 0,auto; 
}
.wall:hover {
  background-color: red;
}
.floor {
  background-color: lightgrey;
  cursor:url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'  width='22' height='26' viewport='0 0 100 100' style='fill:black;font-size:13px;'><text y='50%'>😀</text></svg>") 16 0,auto; 
}

.border-left {
  border-left: 2px solid black;
}

.border-right {
  border-right: 2px solid black;
}

.border-top {
  border-top: 2px solid black;
}

.border-bottom {
  border-bottom: 2px solid black;
}

.clock {
  order: 0;
  flex: 0 1 auto;
  align-self: center;
  margin-top: 24px;
  font-weight: 400;
  font-size: 18px;
  color: black;
  font-family: 'Courier New', Courier, monospace;
}

.text {
  color: black;
  font-family: 'Courier New', Courier, monospace;
  font-size: 12px;
}

.background-image {
  display: none;
  min-height: 100vh;
  width: 100%;
  z-index: 100;
  background-image: url(/src/assets/nic-cage-gandalf.webp);
  background-repeat: no-repeat;
  background-position: center;
}
</style>