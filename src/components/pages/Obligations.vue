<template>
  <div id="obligations">
    <div class="blocks-merged">
      <utility-electricity></utility-electricity>
      <utility-gas></utility-gas>
      <utility-water></utility-water>
      <utility-telephone></utility-telephone>
      <utility-internet></utility-internet>
      <utility-cable></utility-cable>
      <utility-security></utility-security>
    </div>
    <next-button nextpage="miscellaneous"></next-button>
    <br>
    <center>
      <button class="asta-btn back-btn" @click="back">
        <span class="fa fa-arrow-left"></span> Back
      </button>
    </center>
  </div>
</template>

<script>

  import UtilityElectricity from '../blocks/UtilityElectricity.vue';
  import UtilityGas from '../blocks/UtilityGas.vue';
  import UtilityWater from '../blocks/UtilityWater.vue';
  import UtilityTelephone from '../blocks/UtilityTelephone.vue';
  import UtilityInternet from '../blocks/UtilityInternet.vue';
  import UtilityCable from '../blocks/UtilityCable.vue';
  import UtilitySecurity from '../blocks/UtilitySecurity.vue';
  import NextButton from '../interface/NextButton.vue';

  export default {
    name: 'obligations',
    components: {
      UtilityElectricity,
      UtilityGas,
      UtilityWater,
      UtilityTelephone,
      UtilityInternet,
      UtilityCable,
      UtilitySecurity,
      NextButton
    },
    methods: {
      back() {
          this.$router.push({ name: 'terms' });
      }
    },
    data () {
      return {

      };
    }
  };

</script>
