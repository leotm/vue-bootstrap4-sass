<template>
  <div id="miscellaneous">
    <property-sublet></property-sublet>
    <keys-number></keys-number>
    <property-inspection></property-inspection>
    <additional-info></additional-info>
    <next-button nextpage="summary"></next-button>
    <br>
    <center>
      <button class="asta-btn back-btn" @click="back">
        <span class="fa fa-arrow-left"></span> Back
      </button>
    </center>
  </div>
</template>

<script>

  import PropertySublet from '../blocks/PropertySublet.vue';
  import KeysNumber from '../blocks/KeysNumber.vue';
  import PropertyInspection from '../blocks/PropertyInspection.vue';
  import AdditionalInfo from '../blocks/AdditionalInfo.vue';
  import NextButton from '../interface/NextButton.vue';

  export default {
    name: 'miscellaneous',
    components: {
      PropertySublet,
      KeysNumber,
      PropertyInspection,
      AdditionalInfo,
      NextButton
    },
    methods: {
      back() {
          this.$router.push({ name: 'obligations' });
      }
    },
    data () {
      return {

      };
    }
  };

</script>
