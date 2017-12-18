<template>
    <div id="tenants" class="asta-block" v-if="block.fields.tenants.length"  @click="blockClick">
      <div v-for="(tenant, key) in block.fields.tenants" @click="tenantClick(key)">
        <hr :id="'tenant_' + key">
        <h2 class="header" :class="{valid: block.fields.tenants[key].valid, invalid: block.fields.tenants[key].valid == false }">
          Tenant {{key + 1}} <span v-if="key === 0">(primary)</span> details:
        </h2>
        <div class="asta-question">
          <div class="asta-inputs">
            <div class="col_1_3">
                <select class="asta-input" v-validate="'required|not_in:null'" v-model="block.fields.tenants[key].fields.title.value" @blur="validateBlock(key,$event)" data-vv-name="title" :data-vv-scope="'tenant_' + key">
                  <option value="null" disabled>Title...</option>
                  <option v-for="option of constants.TITLES" v-bind:value="option.id">{{option.label}}</option>
                </select>
            </div>
            <div class="col_1_3">
                <input class="asta-input" v-validate="'required|alpha_spaces'" v-model="block.fields.tenants[key].fields.firstName.value" @blur="validateBlock(key,$event)" data-vv-name="firstName" :data-vv-scope="'tenant_' + key" type="text" placeholder="First Name">
            </div>
            <div class="col_1_3">
                <input class="asta-input" v-validate="'required|alpha_spaces'" v-model="block.fields.tenants[key].fields.lastName.value" @blur="validateBlock(key,$event)" data-vv-name="lastName" :data-vv-scope="'tenant_' + key" type="text" placeholder="Last Name">
            </div>
          </div>
          <div class="asta-inputs">
            <div class="col_1_2">
                <input class="asta-input" v-validate="'required|email'" v-model="block.fields.tenants[key].fields.email.value" @blur="validateBlock(key,$event)" data-vv-name="email" :data-vv-scope="'tenant_' + key" type="text" placeholder="Email Address">
            </div>
            <div class="col_1_2">
                <div class="phone_container" :class="isFieldLoadingClass('tenantPhone_'+ key)">
                  <input class="asta-input" data-vv-validate-on="blur" v-validate="'required|verify_number:tenantPhone_' + key" v-model="block.fields.tenants[key].fields.phoneNumber.value" @blur="validateBlock(key,$event)" :data-vv-scope="'tenant_' + key" data-vv-name="phoneNumber" type="text" placeholder="Mobile Number">
                </div>
            </div>
          </div>
        </div>
        <div class="block-errors">
          <span v-show="fields['$tenant_' + key] && fields['$tenant_' + key].title && fields['$tenant_' + key].title.invalid && fields['$tenant_' + key].title.touched && !fields['$tenant_' + key].title.pristine" class="is-error">{{ errors.first('tenant_'+ key +'.title') }}</span>
          <span v-show="fields['$tenant_' + key] && fields['$tenant_' + key].firstName && fields['$tenant_' + key].firstName.invalid && fields['$tenant_' + key].firstName.touched && !fields['$tenant_' + key].firstName.pristine" class="is-error">{{ errors.first('tenant_'+ key +'.firstName') }}</span>
          <span v-show="fields['$tenant_' + key] && fields['$tenant_' + key].lastName && fields['$tenant_' + key].lastName.invalid && fields['$tenant_' + key].lastName.touched && !fields['$tenant_' + key].lastName.pristine" class="is-error">{{ errors.first('tenant_'+ key +'.lastName') }}</span>
          <span v-show="fields['$tenant_' + key] && fields['$tenant_' + key].email && fields['$tenant_' + key].email.invalid && fields['$tenant_' + key].email.touched && !fields['$tenant_' + key].email.pristine" class="is-error">{{ errors.first('tenant_'+ key +'.email') }}</span>
          <span v-show="fields['$tenant_' + key] && fields['$tenant_' + key].phoneNumber && fields['$tenant_' + key].phoneNumber.invalid && fields['$tenant_' + key].phoneNumber.touched && !fields['$tenant_' + key].phoneNumber.pristine && !fields['$tenant_' + key].phoneNumber.pending" class="is-error">{{ errors.first('tenant_'+ key +'.phoneNumber') }}</span>
        </div>
      </div>
      <div class="block-errors" v-if="block.errors.length">
         <span v-for="message of block.errors" class="is-error">{{message}}</span>
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
    name: 'tenants',
    mixins: [blockMixin],
    components: {
      SweetModal,
      SweetModalTab
    },
    methods : {
      validateBlock(key, event) {

        let scope = 'tenant_' + key;

        let field = $(event.target);
        let this_ = this;
        let field_name = field.data('vv-name');
        let field_scope = field.data('vv-scope');

        this.$validator.flag( field_scope + '.' +field_name , {
          pristine: false,
          touched: true,
          untouched: false
        });

        this.$validator.validateAll(scope).then(result => {
          if (result) {
            this.block.fields.tenants[key].valid = true;
          }
          else {
            if(this.block.fields.tenants[key].valid == true) {
              this.block.fields.tenants[key].valid = false;
            }
          }

          let tenants_valid = true;

          for (let tenant of this.block.fields.tenants) {
            if (!tenant.valid) {
              tenants_valid = false;
            }
          }

          this.block.valid = tenants_valid;
          this.$store.commit('updateBlock', this.block);

        });

      },
      tenantClick(key) {

        for(let i = 0; i<key; i++) {
          let scope = 'tenant_' + i;

          this.$validator.validateAll(scope);
          if(!this.block.fields.tenants[i].valid) {
            this.block.fields.tenants[i].valid = false;

            for(var j in this.block.fields.tenants[i].fields) {

                this.$validator.flag( scope + '.' + j , {
                  touched: true,
                  untouched: false,
                  pristine: false
                });

            }

            this.$store.commit('updateBlock', this.block);

          }

        }
      }
    }
  };

</script>
