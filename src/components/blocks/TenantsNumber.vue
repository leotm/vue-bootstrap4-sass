<template>
  <div id="tenants-number" class="asta-block" @click="blockClick">
    <h2 class="header" :class="validateBlock()">Number of tenants?</h2>
    <div class="asta-question">
      <div class="asta-inputs">
          <div class="col_1_2">
              <div class="select-input">
                <select class="asta-input" v-validate="'required|not_in:null'" v-model="block.fields.noTenants.value" data-vv-name="noTenants" @change="initTenants();validateBlock($event)">
                  <option value="null" disabled>Please Select...</option>
                  <option v-for="option of constants.TENANTS_NUMBER" v-bind:value="option.id">{{option.label}}</option>
                </select>
              </div>
          </div>
      </div>
    </div>
    <div class="block-errors">
      <span v-show="errors.has('noTenants')" class="is-error">{{ errors.first('noTenants') }}</span>
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
    name: 'tenants-number',
    mixins: [blockMixin],
    components: {
      SweetModal,
      SweetModalTab
    },
    methods : {
      initTenants() {
        this.$store.commit('initTenants',this.block.fields.noTenants.value)
      }
    }
  };

</script>
