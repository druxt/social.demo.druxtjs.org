<template>
  <DuiCard>
    <DruxtView
      view-id="activity_stream_group"
      display-id="block_stream_group"
      :arguments="[groupId]"
    />
  </DuiCard>
</template>

<script>
export default {
  props: {
    entity: {
      type: Object,
      required: true
    },
    groupId: {
      type: String,
      require: true
    }
  }
}
</script>
