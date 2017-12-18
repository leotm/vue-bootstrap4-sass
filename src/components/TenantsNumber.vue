<template>
  <b-container>
    <b-row class="section-wrapper">
      <b-col xs="12" sm="12" md="12" lg="12" class="px-2">
        <p class="section-title">{{ sectionTitle }}</p>
      </b-col>
      <b-col xs="12" sm="12" md="8" lg="8" class="p-2">
        <b-input-group>
          <b-form-input></b-form-input>
        </b-input-group>
      </b-col>
      <b-col xs="12" sm="12" md="4" lg="4" class="p-2">
        <b-button class="w-100 btn-lightblue">
          Tenants Number
        </b-button>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
  export default {
    name: 'TenantsNumber',
    props: {
      sectionTitle: {
        type: String,
        default: 'foooo'
      }
    }
  }
</script>

<style scoped>

</style>
