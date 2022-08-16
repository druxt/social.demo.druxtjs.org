<template>
  <DuiCard>
    <div v-html="entity.attributes.field_group_description.processed" />
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
