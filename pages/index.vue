<template>
  <div class="container">
    <id-card></id-card>
    <sns-card></sns-card>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'
  import IdCard from '../components/id_card.vue';
  import SnsCard from '../components/sns_card.vue';

  export default Vue.extend({

    components: {IdCard, SnsCard},
  });
</script>


<style lang="scss">

</style>
