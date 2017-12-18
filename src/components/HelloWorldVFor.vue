<template>
  <div class="container">
    <b-card title="How many tenants?">
      <b-form-select v-model="selected" :options="options" class="mb-3"></b-form-select>
    </b-card>
    <p v-repeat="selected">

    </p>
    <div v-for="(tenant, n) in tenants" :key="tenant.id">
      <ul>
        <li :tenant="tenant">
          {{ tenant.firstName }},
          {{ tenant.lastName }},
          {{ n }}
        </li>
      </ul>
    </div>
  </div>
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
