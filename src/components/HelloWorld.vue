<template>
  <b-container>
    <b-row>
      <b-col sm="12" class="mb-1">
        <b-card title="How many tenants?" >
          <b-form-select v-model="selected" :options="options"></b-form-select>
        </b-card>
      </b-col>
    </b-row>
    <div v-for="(tenant, n) in selected" :key="tenant.id">
    <b-row>
      <b-col sm="12" class="mb-1">
          <b-card>
            Import TenantsNumber component and repeat here,
            Number: {{ tenant }},
            Index: {{ n }}
          </b-card>
      </b-col>
    </b-row>
    </div>
  </b-container>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      selected: null,
      options: [
        { value: null, text: 'Please select how many tenants', disabled: true },
        { value: 1, text: '1' },
        { value: 2, text: '2' },
        { value: 3, text: '3' }
      ],
      tenants: [
        {
          firstName: 'Tom',
          lastName: 'Jones'
        }
      ]
    }
  }
}
</script>

<style scoped>

</style>
