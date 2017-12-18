<template>
  <div>
    <b-form-input v-model="firstName" type="text" placeholder="First name"></b-form-input>
    <p>Value: {{ text1 }}</p>
  </div>
</template>

<script>
export default {
  name: 'NewTenant',
  data () {
    return {
      data: 'value'
    }
  }
}
</script>

<style scoped>

</style>
