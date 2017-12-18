<template>
  <div id="tenancy-start" class="asta-block" @click="blockClick">
      <div class="asta-question">
        <h2 class="header" :class="validateBlock()">Tenancy start date:</h2>
        <div class="asta-inputs">
            <div class="col_1_2">
              <input type="date" class="asta-input" :min="tenancyStartMinDate" data-vv-validate-on="blur" placeholder="YYYY-MM-DD" v-validate="'required|date_format:YYYY-MM-DD'" v-model="block.fields.tenancyStart.value" data-vv-name="tenancyStart"  v-mask="'####-##-##'">
            </div>
        </div>
      </div>
      <div class="block-errors">
        <span v-show="errors.has('tenancyStart')" class="is-error">{{ errors.first('tenancyStart') }}</span>
      </div>
    </div>
</template>

<script>

  import blockMixin from '../../mixins/block.js';
  import SweetModal from 'sweet-modal-vue/src/components/SweetModal.vue';
  import SweetModalTab from 'sweet-modal-vue/src/components/SweetModalTab.vue';

  export default {
    name: 'tenancy-start',
    mixins: [blockMixin],
    components: {
      SweetModal,
      SweetModalTab
    },
    computed : {
      tenancyStartMinDate() {
          return this.$moment().format('YYYY-MM-DD');
      }
    }
  };

</script>
