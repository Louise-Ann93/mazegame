<template>
<div class="wrapper">

  <div class="map">
      
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

      <div class="floor border-left border-right">
        Start
      </div>

      <div @mouseover="mouseWarning"
      class="wall border-bottom">
      </div>

      <div @mouseover="wellDone" class="floor border-left border-right">
        Finish
      </div>
     
     <div @mouseover="mouseWarning"
      class="wall border-bottom">
      </div>
      <div @mouseover="mouseWarning"
      class="wall border-bottom border-right">
      </div>
  </div>

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
        };
    },
    watch: {
      warning () {
       if(this.warning == 3) {
         alert('Fail!')
         this.warning = 0
       } 
      },
    },
    methods: {
        getMouseCoOrd(event) {
            this.pointerX = event.clientX;
            this.pointerY = event.clientY;
            console.log(pointerX)
            console.log(pointerY)
        },
        mouseWarning() {
            this.warning++;
            console.log(this.warning)
        },
        wellDone () {
          alert('CONGRATS YOU WON')
        }
    },
}

</script>

<style scoped>

.wrapper {
  display: flex;
  justify-content: center;

}
.map {
text-align: center;
display: grid;
grid-template: repeat(6, 50px) / repeat(6, 50px);
}

.wall {
  background-color: green;
}
.wall:hover {
  background-color: red;
}
.floor {
  background-color: lightgrey;
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
</style>