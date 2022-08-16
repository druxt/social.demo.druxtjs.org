<template>
  <DuiCard
    class="my-4"
    :title="entity.attributes.label"
    side
  >
    <template #image>
      <img src="https://placeimg.com/200/280/arch" alt="Movie">
    </template>

    <template #actions>
      <NuxtLink :to="to" tag="button" class="btn btn-ghost">Read more</NuxtLink>
    </template>
  </DuiCard>
</template>

<script>
import { DruxtEntityMixin } from 'druxt-entity'
export default {
  mixins: [DruxtEntityMixin],
  computed: {
    to: ({ entity }) => `group/${entity.attributes.drupal_internal__id}/stream`
  }
}
</script>
