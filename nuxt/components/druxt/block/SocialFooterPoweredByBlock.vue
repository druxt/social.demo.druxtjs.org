<template>
  <div v-html="text" />
</template>

<script>
import { DruxtBlocksBlockMixin } from 'druxt-blocks'

export default {
  mixins: [DruxtBlocksBlockMixin],
  computed: {
    text: ({ settings }) => settings.text.value + '<p>Decoupled with Druxt</p>'
  }
}
</script>
