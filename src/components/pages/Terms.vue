<template>
  <div id="terms">
    <div class="blocks-merged">
      <tenancy-start></tenancy-start>
      <tenancy-duration></tenancy-duration>
      <tenancy-end></tenancy-end>
    </div>
    <div class="blocks-merged">
      <rent-frequency></rent-frequency>
      <rent-amount></rent-amount>
      <rent-date></rent-date>
      <rent-date-weekly></rent-date-weekly>
      <rent-method></rent-method>
    </div>
    <div class="blocks-merged">
      <deposit-required></deposit-required>
      <deposit-amount></deposit-amount>
      <deposit-scheme></deposit-scheme>
    </div>
    <next-button nextpage="obligations"></next-button>
    <br>
    <center>
      <button class="asta-btn back-btn" @click="back">
        <span class="fa fa-arrow-left"></span> Back
      </button>
    </center>
  </div>
</template>

<script>

  import TenancyStart from '../blocks/TenancyStart.vue';
  import TenancyDuration from '../blocks/TenancyDuration.vue';
  import TenancyEnd from '../blocks/TenancyEnd.vue';
  import RentFrequency from '../blocks/RentFrequency.vue';
  import RentAmount from '../blocks/RentAmount.vue';
  import RentDate from '../blocks/RentDate.vue';
  import RentDateWeekly from '../blocks/RentDateWeekly.vue';
  import RentMethod from '../blocks/RentMethod.vue';
  import DepositRequired from '../blocks/DepositRequired.vue';
  import DepositAmount from '../blocks/DepositAmount.vue';
  import DepositScheme from '../blocks/DepositScheme.vue';
  import NextButton from '../interface/NextButton.vue';

  export default {
    name: 'terms',
    components: {
      TenancyStart,
      TenancyDuration,
      TenancyEnd,
      RentFrequency,
      RentAmount,
      RentDate,
      RentDateWeekly,
      RentMethod,
      DepositRequired,
      DepositAmount,
      DepositScheme,
      NextButton
    },
    methods: {
      back() {
          this.$router.push({ name: 'property' });
      }
    },
    data () {
      return {

      };
    }
  };

</script>
