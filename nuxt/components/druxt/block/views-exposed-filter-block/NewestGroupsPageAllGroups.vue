<template>
  <div class="card bg-base-100 shadow-xl">
    <div class="card-body" v-if="!$fetchState.pending">
      <h2 class="card-title">Filter</h2>

      <!-- @TODO - This isn't hooked up to anything at the moment. -->
      <DuiSelect
        :label="filters.field_group_allowed_join_method_value.expose.label"
        :options="options"
      />

      <div class="card-actions justify-end">
        <button class="btn btn-primary" v-text="displayOptions.exposed_form.options.submit_button" />
      </div>
    </div>
    <div v-else />
  </div>
</template>

<script>
import { DruxtBlocksBlockMixin } from 'druxt-blocks'
import { DrupalJsonApiParams } from 'drupal-jsonapi-params'

export default {
  mixins: [DruxtBlocksBlockMixin],

  data: () => ({
    view: {}
  }),

  async fetch() {
    this.view = (((await this.$store.dispatch('druxt/getCollection', {
      type: 'view--view',
      query: new DrupalJsonApiParams().addFilter('drupal_internal__id', 'newest_groups')
    })) || {}).data || [])[0] || undefined
  },

  computed: {
    displayOptions: ({ view }) => ((((view || {}).attributes || {}).display || {}).default || {}).display_options || {},
    filters: ({ displayOptions }) => displayOptions.filters,
    options: () => [
      { id: undefined, label: '- Any -' },
      { id: 'direct', label: 'Open to join' },
      { id: 'added', label: 'Invite only' },
      { id: 'request', label: 'Request to join' },
    ],
  }
}
</script>
