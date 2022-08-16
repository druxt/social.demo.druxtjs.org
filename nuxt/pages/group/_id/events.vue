<template>
  <DruxtView
    view-id="group_events"
    display-id="page_group_events"
    :arguments="[groupId]"
  />
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
