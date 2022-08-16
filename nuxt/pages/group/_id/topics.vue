<template>
  <DruxtView
    view-id="group_topics"
    display-id="page_group_topics"
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
