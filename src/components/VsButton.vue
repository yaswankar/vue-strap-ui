<template>
  <button
    id="button"
    :class="className"
    :style="cssVars"
    @click="$emit('click', $event)">
      <slot>Submit</slot>
  </button>
</template>
<script>
export default {
    name: 'VsButton',
    props: {
      width: {
        type: String,
        default: '100'
      },
      bgColor: {
        type: String,
        default: '#316cad'
      },
      color: {
        type: String,
        default: '#fffff'
      },
      height: {
        type: String,
        default: '40'
      },
      radius: {
        type: String,
        default: '20%'
      },
      className: {
        type: String,
        default: 'button'
      }
    },
    computed: {
      cssVars() {
        return {
          '--bg-color': this.bgColor,
          '--fg-color': this.color,
          '--width': `${this.width}px`,
          '--height': `${this.height}px`,
          '--light-color': this.convertToRGB(this.bgColor),
          '--radius': `${this.radius}px`
        }
      },
      convertToRGB() {
        return hex => {
          var result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
          if(result){
              var r= parseInt(result[1], 16);
              var g= parseInt(result[2], 16);
              var b= parseInt(result[3], 16);
              return r+","+g+","+b;
          } 
          return null;
        }
      }

    }
};
</script>
<style lang="scss" scoped>
:root {
  --color: 255, 0, 0;
  --alpha: 0.8;
}

.button {
  padding: 10px 15px;
  box-shadow: 0px 0px 12px -2px rgba(0, 0, 0, 0.5);
  line-height: 1.25;
  background: var(--bg-color);
  text-decoration: none;
  color: var(--fg-color);
  font-size: 16px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  position: relative;
  transition: background-color 0.6s ease;
  overflow: hidden;
  border: none;
  border-radius: var(--radius);
  &:after {
    content: "";
    position: absolute;
    width: 0;
    height: 0;
    top: 50%;
    left: 50%;
    transform-style: flat;
    transform: translate3d(-50%, -50%, 0);
    border-radius: 100%;
    transition: width 0.3s ease, height 0.3s ease;
  }
  &:focus, &:hover {
    background: rgba(var(--light-color), 0.8);
  }
}
.button:active:after {
  width: 300px;
  height: 300px;
}
.btn-outline {
  &:hover, &:focus {
    box-shadow: inset 0 0 0 2em var(--hover);
  }
}
</style>