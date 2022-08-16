<template>
  <div
    class="card bg-base-100 shadow-xl"
    :class="{
      'card-side': side
    }"
  >
    <figure v-if="$scopedSlots.image"><slot name="image" /></figure>
    <div class="card-body">
      <h2 class="card-title" v-if="title" v-text="title" />
      <slot />
      <div v-if="$scopedSlots.actions" class="card-actions justify-end">
        <slot name="actions" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    side: {
      type: Boolean,
      default: false
    },
    title: {
      type: String,
      default: undefined
    }
  }
}
</script>
