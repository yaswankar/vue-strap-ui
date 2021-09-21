<template>
  <button
    id="button"
    class="btn"
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
    },
    computed: {
      cssVars() {
        return {
          '--bg-color': this.bgColor,
          '--fg-color': this.color,
          '--width': `${this.width}px`,
          '--height': `${this.height}px`,
          '--light-bg-color': this.convertToRGB(this.bgColor),
          '--light-fg-color': this.convertToRGB(this.color),
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
button {
  padding: 10px 15px;
  box-shadow: 0px 0px 12px -2px rgba(0, 0, 0, 0.5);
  line-height: 1.25;
  text-decoration: none;
  font-size: 16px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  position: relative;
  transition: background-color 0.6s ease;
  overflow: hidden;
  border: none;
  border-radius: var(--radius);
  height: var(--height);
  width: var(--width);
  &:hover {
    cursor: pointer;
  }
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
}
.btn-fill {
  background: var(--bg-color);
  color: var(--fg-color);
  &:focus, &:hover {
    background: rgba(var(--light-bg-color), 0.8);
  }
}

.btn-outline {
  background: white;
  color: var(--fg-color);
  border: 2px solid var(--fg-color);
  font-weight: bold;
  &:focus, &:hover {
    background: rgb(var(--light-bg-color));
    color: #ffffff;
  }
}

// type - success
.btn-fill.success {
  background: var(--success);
  color: white;
  &:focus, &:hover {
    background: rgba(10, 192, 80, 0.8);
  }
}
.btn-outline.success {
  background: white;
  color: var(--success);
  border: 2px solid var(--success);
  &:focus, &:hover {
    background: rgb(10, 192, 80);
    color: #ffffff;
  }
}

//type - danger
.btn-fill.danger {
  background: var(--danger);
  color: white;
  &:focus, &:hover {
    background: rgba(252, 94, 88, 0.8);
  }
}
.btn-outline.danger {
  background: white;
  color: var(--danger);
  border: 2px solid var(--danger);
  &:focus, &:hover {
    background: rgb(252, 94, 88);
    color: #ffffff;
  }
}

//type - medium
.btn-fill.medium {
  background: var(--medium);
  color: white;
  &:focus, &:hover {
    background: rgba(96, 105, 112, 0.8);
  }
}
.btn-outline.medium {
  background: white;
  color: var(--medium);
  border: 2px solid var(--medium);
  &:focus, &:hover {
    background: rgb(96, 105, 112);
    color: #ffffff;
  }
}
</style>