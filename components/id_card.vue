<template>
  <div class="id-card">
    <div class="logo-container">
      <div class="logo logo-loading" :class="{'logo-loaded': imageURL.length > 0}">
        <span>・</span>
        <span>・</span>
        <span>・</span>
      </div>
      <transition name="logo-in">
        <div v-show="imageURL.length > 0" class="logo" :style="{'background-image': 'url('+imageURL+')' }"></div>
      </transition>
    </div>
    <h1 class="id">MOX</h1>
    <p class="id-name">Masaki&nbsp;Furukawa</p>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'

  export default Vue.extend({
    data() {
      return {
        imageURL: '',
      }
    },
    components: {},
    mounted(): void {
      const configInit: RequestInit = {
        method: 'GET',
        mode: 'cors',
        cache: 'force-cache',
      };
      fetch('/logo.png', configInit).then((response) => {
        if (response.ok) {
          return response.blob();
        }
        throw new Error('Network response was not ok.');
      }).then((imageBlob) => {
        this.imageURL = URL.createObjectURL(imageBlob);
      });
    }
  });
</script>


<style lang="scss">
  .id-card {
    $width: 250px;
    position: absolute;
    width: $width;
    top: 10%;
    left: 50%;
    transform: translateX(-50%);

    .logo-container {
      width: 100%;

      .logo {
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: $width/2;
        width: $width;
        height: $width;
        background-repeat: no-repeat;
        background-size: contain;
        background-position: center;
        border-radius: 50%;
        border: solid 2px white;
        box-shadow: 0 0 15px white;
        z-index: 2;
      }

      .logo-loading {
        box-shadow: 0 0 0 white;
        background-color: rgba(white, .1);
        font-size: $width/3;

        span {
          &:nth-child(1) {
            animation: loadingOpacity .5s linear infinite;
          }

          &:nth-child(2) {
            animation: loadingOpacity .5s linear .1s infinite;
          }

          &:nth-child(3) {
            animation: loadingOpacity .5s linear .2s infinite;
          }
        }
      }

      .logo-loaded {
        margin-bottom: -$width;
      }
    }

    .id {
      margin-top: 25px;
      text-align: center;
      letter-spacing: 12px;
      animation: idFadeIn ease .3s;
    }

    .id-name {
      text-align: center;
      font-size: 12px;
      letter-spacing: 3px;
      animation: idNameFadeIn ease .3s;
    }
  }

  @keyframes loadingOpacity {
    0% {
      opacity: 1;
    }
    50% {
      opacity: .2;
    }
    100% {
      opacity: 1;
    }
  }

  @keyframes idFadeIn {
    0% {
      opacity: 0;
      transform: translateX(-45px);
    }
    100% {
      opacity: 1;
      transform: none;
    }
  }

  @keyframes idNameFadeIn {
    0% {
      opacity: 0;
      transform: translateX(45px);
    }
    100% {
      opacity: 1;
      transform: none;
    }
  }

  .logo-in-enter-active, .logo-in-leave-active {
    will-change: opacity;
    transition: opacity .3s, transform .3s ease;
  }

  .logo-in-enter, .logo-in-leave-to {
    opacity: 0;
    transform: rotate(-15deg) scale(1.2);
  }
</style>
