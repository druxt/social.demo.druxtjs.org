<template>
  <ClientOnly placeholder="Redirecting...">
    {{ loginRedirect() }}
  </ClientOnly>
</template>

<script>
export default {
  methods: {
    loginRedirect() {
      this.$nuxt.$auth.loginWith('drupal-authorization_code')
      return 'Redirecting...'
    }
  }
}
</script>
