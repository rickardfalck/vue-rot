<template>
  <svg viewBox="0,0,100,100" class="icon" v-on:click="toggleMenuBtn">
      <circle cx="50" cy="50" class="button-box" r="40"/>
      <transition name="openfx">
        <svg v-if="open">
          <path class="line" d="M65 50 L 35 50Z"/>
          <polygon points="50,35 30,50 50,65" class="arrow"/>
        </svg>
        <svg v-else>
          <path d="M30 35 L 70 35Z" class="line"/>
          <path d="M30 50 L 70 50Z" class="line"/>
          <path d="M30 65 L 70 65Z" class="line"/>
        </svg>
      </transition>
  </svg>
</template>

<script>
export default {
  props:{
    left: String,
    size: Number,
  },
  emits: ['openChanged'],
  data(){
    return {
      open: false
    }
  },
  methods: {
    toggleMenuBtn(){
      this.open = ! this.open;
      this.$emit('openChanged', this.open);
    }
  }
}
</script>

<style scoped>

    .arrow {
        fill: white;
        rotate: 180;
    }

    .button-box {
        fill: #2c3e50;
    }

    .icon {
        height: 36px;
        width: 36px;
        top: 50px;
        left: v-bind(left);
        position: fixed;
        cursor: pointer;
        
    }
    
    .line {
      stroke: white;
      stroke-width: 5px;
    }

    .openfx-enter-active {
      animation: fading 0.5s reverse;
    }
    .openfx-leave-active {
      animation: fading 0.5s;
    }

    @keyframes fading {
      0% {opacity: 100%; transform: rotate(0);}
      100% {opacity: 0%; transform: rotate(180);}
    }

    @keyframes shift-in {
      0%   {transform:rotateY(0deg);}
      50%  {transform:rotateY(90deg);}
      100%  {transform:rotateY(180deg);}
    }

</style>