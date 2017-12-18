<template>
  <div id="parties">
    <div class="blocks-merged">
      <landlord-type></landlord-type>
      <landlords-number></landlords-number>
      <landlords></landlords>
      <company-details></company-details>
      <landlord-details></landlord-details>
    </div>
    <div class="blocks-merged">
      <main-contact></main-contact>
      <select-landlord></select-landlord>
      <add-contact></add-contact>
    </div>
    <div class="blocks-merged">
      <tenants-number></tenants-number>
      <tenants></tenants>
    </div>
    <div class="blocks-merged">
      <guarantor-required></guarantor-required>
      <guarantor-details></guarantor-details>
    </div>
    <next-button nextpage="property"></next-button>
  </div>
</template>

<script>

  import LandlordType from '../blocks/LandlordType.vue';
  import LandlordsNumber from '../blocks/LandlordsNumber.vue';
  import Landlords from '../blocks/Landlords.vue';
  import CompanyDetails from '../blocks/CompanyDetails.vue';
  import LandlordDetails from '../blocks/LandlordDetails.vue';
  import MainContact from '../blocks/MainContact.vue';
  import SelectLandlord from '../blocks/SelectLandlord.vue';
  import AddContact from '../blocks/AddContact.vue';
  import TenantsNumber from '../blocks/TenantsNumber.vue';
  import Tenants from "../blocks/Tenants.vue";
  import GuarantorRequired from "../blocks/GuarantorRequired.vue";
  import GuarantorDetails from "../blocks/GuarantorDetails.vue";
  import NextButton from '../interface/NextButton.vue';

  export default {
    name: 'parties',
    components: {
      LandlordType,
      LandlordsNumber,
      Landlords,
      CompanyDetails,
      LandlordDetails,
      MainContact,
      SelectLandlord,
      AddContact,
      TenantsNumber,
      Tenants,
      GuarantorRequired,
      GuarantorDetails,
      NextButton
    },
    data () {
      return {

      };
    }
  };

</script>
