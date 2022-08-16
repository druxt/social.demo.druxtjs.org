<template>
  <div class="form-control w-full max-w-xs">
    <label class="label">
      <span class="label-text" v-text="label" />
    </label>
    <select class="select select-bordered">
      <option v-for="option of options" :key="option.id" v-text="option.label" />
    </select>
  </div>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      require: true
    },
    options: {
      type: Array,
      required: true
    }
  }
}
</script>
