<template>
  <div id="property">
    <property-address></property-address>
    <property-parking></property-parking>
    <property-furnished></property-furnished>
    <next-button nextpage="terms"></next-button>
    <br>
    <center>
      <button class="asta-btn back-btn" @click="back">
        <span class="fa fa-arrow-left"></span> Back
      </button>
    </center>
  </div>
</template>

<script>

  import PropertyAddress from '../blocks/PropertyAddress.vue';
  import PropertyParking from '../blocks/PropertyParking.vue';
  import PropertyFurnished from '../blocks/PropertyFurnished.vue';
  import NextButton from '../interface/NextButton.vue';

  export default {
    name: 'property',
    components: {
      PropertyAddress,
      PropertyParking,
      PropertyFurnished,
      NextButton
    },
    methods: {
      back() {
          this.$router.push({ name: 'parties' });
      }
    },
    data () {
      return {

      };
    }
  };

</script>
