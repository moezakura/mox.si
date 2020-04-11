<template>
  <div class="sns-card">
    <h2>contact</h2>
    <ul class="sns-list">
      <li class="twitter">
        <a href="//twitter.com/__MOX__" target="_blank">
          <fa :icon="faTwitter"/>
          <p class="sns-id">@__mox__</p>
        </a>
      </li>
      <li class="github">
        <a href="//github.com/moezakura" target="_blank">
          <fa :icon="faGithub"/>
          <p class="sns-id">moezakura</p>
        </a>
      </li>
      <li class="mail">
        <a>
          <fa :icon="faMail"/>
          <p class="sns-id">Click to show</p>
        </a>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'
  import {faTwitter, faGithub} from '@fortawesome/free-brands-svg-icons'
  import {faEnvelope} from '@fortawesome/free-solid-svg-icons'

  export default Vue.extend({
    computed: {
      faTwitter() {
        return faTwitter
      },

      faGithub() {
        return faGithub
      },

      faMail() {
        return faEnvelope
      }
    }
  });
</script>


<style lang="scss">
  .sns-card {
    $width: 250px;
    position: absolute;
    min-width: $width;
    max-width: $width * 2;
    top: 55%;
    left: 50%;
    transform: translateX(-50%);

    h2 {
      text-align: center;
      animation: snsCardFadeIn ease .3s;
    }

    .sns-list {
      list-style: none;
      margin: 8px 0 0 0;
      padding: 0;

      li {
        $size: 45px;
        height: $size;
        font-size: 18px;
        font-weight: bold;
        letter-spacing: 1.5px;
        margin: 3px 0;

        a {
          display: flex;
          align-items: center;
          height: $size;
          color: white;
          text-decoration: none;
          padding: 0 15px;

          p {
            display: flex;
            width: auto;
            height: $size;
            align-items: center;
            margin: 0 0 0 10px;
          }

          svg {
            margin: 0 10px 0 0;
          }
        }

        &::before {
          display: block;
          height: $size;
          width: 5px;
          content: ' ';
          margin-bottom: -$size;
          opacity: 0;
          transform: translateX(-5px);
          transition: opacity .3s ease, transform .3s ease;
        }

        &:hover:before {
          opacity: 1;
          transform: translateX(0);
        }

        &.twitter::before {
          background-color: rgb(29, 161, 242);
        }

        &.github::before {
          background-color: rgb(255, 211, 61);
        }

        &.mail::before {
          background-color: rgb(212, 70, 56);
        }

        &.mail {
          cursor: pointer;

          p {
            font-size: 16px;
            font-weight: normal;
          }
        }
      }
    }
  }

  @keyframes snsCardFadeIn {
    0% {
      opacity: 0;
      transform: translateY(-45px);
    }
    100% {
      opacity: 1;
      transform: none;
    }
  }
</style>
