<template>
  <div id="app">
    <VButton class="desintegrate-button" ref="button" @onClick="message"/>

    <button class="toggle-button" :class="{ disabled: disabled }" @click="onCallState">{{ text }}</button>
  </div>
</template>

<script>

import './plugins/particules'

import VButton from './components/Button.vue'

export default {
  name: 'app',
  components: {
    VButton
  },
  data: () => ({
    state: false,
    disabled: false,
  }),
  computed:{
    handler(){
      return this.state ? this.$refs.button.disintegrate : this.$refs.button.integrate
    },
    text(){
      return this.state ? 'integrate' : 'disintegrate' 
    }
  },
  watch:{
    state(value){
      this.disabled = true;
      setTimeout(() =>{ 
        this.disabled = false;
      }, 2000)
    }
  },
  methods:{
    onCallState(){
      this.state = !this.state
      this.handler()
    },
    message(){
      alert('clicked')
    }
  }
}
</script>

<style lang="scss">

@import './base';

#app {
  width: 100vw;
  text-align: center;
  height: 100vh;
  display: flex;
  background-color: #FBAB7E;
  background-image: linear-gradient(62deg, #FBAB7E 0%, #F7CE68 100%);
}

.desintegrate-button{
  position: absolute !important;
  top: 50%;
  left: 50%;
  transform: translate(-50%,calc(-50% - 40px));
}

.toggle-button{
  position: absolute !important;
  top: calc(50% + 40px);
  left: 50%;
  transform: translate(-50%, calc(-50% + 40px));
  background-color: lightsalmon;
  padding: 1rem;
  border-radius: 5px;
  border: 1px solid;
  transition:cubic-bezier(0.075, 0.82, 0.165, 1) 1s all;

  &.disabled{
    background: #ccc;
    border: none;
    opacity: .7;
    color: #fff;
  }
}

</style>
