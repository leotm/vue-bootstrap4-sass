<template>
  <div id="tenancy-duration" class="asta-block" v-if="tenancyStart" @click="blockClick">
    <hr>
      <div class="asta-question">
        <h2 class="header" :class="validateBlock()">How long does the tenancy last?</h2>
        <div class="asta-inputs">
          <p>
            <label class="radio-input"><input type="radio" v-validate="'required'" v-model="block.fields.tenancyDuration.value" value="6_months" data-vv-name="tenancyDuration" name="tenancyDuration"> <i class="fa fa-circle"></i> 6 months {{duration6months}}</label>
          </p>
          <p>
            <label class="radio-input"><input type="radio" v-model="block.fields.tenancyDuration.value" value="12_months" name="tenancyDuration"> <i class="fa fa-circle"></i> 12 months {{duration12months}}</label>
          </p>
          <p>
            <label class="radio-input"><input type="radio" v-model="block.fields.tenancyDuration.value" value="specify" name="tenancyDuration"> <i class="fa fa-circle"></i> Specify end date</label>
          </p>
        </div>
      </div>
      <div class="block-errors">
        <span v-show="errors.has('tenancyDuration')" class="is-error">{{ errors.first('tenancyDuration') }}</span>
      </div>
  </div>
</template>

<script>

  import blockMixin from '../../mixins/block.js';
  import SweetModal from 'sweet-modal-vue/src/components/SweetModal.vue';
  import SweetModalTab from 'sweet-modal-vue/src/components/SweetModalTab.vue';

  export default {
    name: 'tenancy-duration',
    mixins: [blockMixin],
    components: {
      SweetModal,
      SweetModalTab
    },
    computed : {
      tenancyStart() {
        return this.$store.getters.getFieldValue({block : 'tenancy-start', field: 'tenancyStart' });
      },
      duration6months: function () {
          var startDate = this.$moment(this.$store.state.data.blocks['tenancy-start'].fields.tenancyStart.value, 'YYYY-MM-DD');
          var endDate = startDate.add(6, 'months');
          
          return "("+endDate.format('YYYY-MM-DD')+")";
      },
      duration12months: function () {
          var startDate = this.$moment(this.$store.state.data.blocks['tenancy-start'].fields.tenancyStart.value, 'YYYY-MM-DD');
          var endDate = startDate.add(12, 'months');
          
          return "("+endDate.format('YYYY-MM-DD')+")";
      }
    }
  };

</script>
