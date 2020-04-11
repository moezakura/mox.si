<template>
  <div class="sns-card">
    <h2>contact</h2>
    <ul class="sns-list">
      <li>
        <div class="sns-icon"></div>
        <p class="sns-id">@__mox__</p>
      </li>
      <li>
        <div class="sns-icon"></div>
        <p class="sns-id">moezakura</p>
      </li>
      <li>
        <div class="sns-icon"></div>
        <p class="sns-id">xxx@xx.com</p>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'

  export default Vue.extend({});
</script>


<style lang="scss">
  .sns-card {
    $width: 250px;
    position: absolute;
    width: $width;
    top: 55%;
    left: 50%;
    transform: translateX(-50%);

    h2 {
      text-align: center;
    }

    .sns-list {
      list-style: none;
      margin: 8px 0 0 0;
      padding: 0;
    }
  }
</style>
