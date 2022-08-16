<template>
  <h1 v-if="route" class="text-4xl mt-8 mb-16" v-text="route.label" />
  <div v-else />
</template>

<script>
import { DruxtBlocksBlockMixin } from 'druxt-blocks'
import { mapState } from 'vuex'

export default {
  mixins: [DruxtBlocksBlockMixin],
  computed: {
    route: ({ $route, routes }) => routes[$route.fullPath] || {},
    ...mapState({
      routes: state => state.druxtRouter.routes || {}
    })
  }
}
</script>
