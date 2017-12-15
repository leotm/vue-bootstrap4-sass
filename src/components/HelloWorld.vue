<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div>
      <b-button href="#" variant="success">I am a Link</b-button>
    </div>
    <template v-for="(tenant, n) in tenants">
      <ul>
        <li :tenant="tenant">
          {{ tenant.firstName }}
          {{ tenant.lastName }}
        </li>
      </ul>
    </template>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome!',
      tenants: [
        {
          firstName: "Tom",
          lastName: "Jones"
        }
      ]
    }
  }
}
</script>

<style scoped>

</style>
