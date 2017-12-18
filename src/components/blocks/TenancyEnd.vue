<template>
  <div id="tenancy-end" class="asta-block" v-if="tenancyDuration == 'specify'" @click="blockClick">
    <hr>
      <div class="asta-question">
        <h2 class="header" :class="validateBlock()">Tenancy end date:</h2>
        <h2 class="header-small">Please ensure there is a minimum of 6 months.</h2>
        <div class="asta-question">
          <div class="asta-inputs">
              <div class="col_1_2">
                <input type="date" class="asta-input" :min="tenancyEndMinDate" placeholder="YYYY-MM-DD" v-validate="'required|date_format:YYYY-MM-DD'" v-model="block.fields.tenancyEnd.value" data-vv-validate-on="blur" data-vv-name="tenancyEnd"  v-mask="'####-##-##'">
              </div>
          </div>
        </div>
      </div>
      <div class="block-errors">
        <span v-show="errors.has('tenancyEnd')" class="is-error">{{ errors.first('tenancyEnd') }}</span>
      </div>
      <!-- <span class="asta-help-button" @click="helpOpen">Help</span>
      <sweet-modal title="More information" ref="helpModal">
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce rhoncus magna auctor, venenatis odio vel, molestie dui. Aliquam ut semper diam. Vivamus euismod finibus justo id vehicula. Interdum et malesuada fames ac ante ipsum primis in faucibus. Quisque vulputate urna vitae eleifend ultrices. Proin in tellus urna. Aenean tincidunt eu massa nec sollicitudin. Fusce lectus justo, hendrerit eu urna nec, egestas pretium nulla.
        </p>
      </sweet-modal> -->
    </div>
</template>

<script>

  import blockMixin from '../../mixins/block.js';
  import SweetModal from 'sweet-modal-vue/src/components/SweetModal.vue';
  import SweetModalTab from 'sweet-modal-vue/src/components/SweetModalTab.vue';

  export default {
    name: 'tenancy-end',
    mixins: [blockMixin],
    components: {
      SweetModal,
      SweetModalTab
    },
    computed : {
      tenancyDuration() {
        return this.$store.getters.getFieldValue({block : 'tenancy-duration', field: 'tenancyDuration' });
      },
      tenancyEndMinDate() {
          return this.$moment().format('YYYY-MM-DD');
      }
    }
  };

</script>
