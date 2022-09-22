<template>
  <div class="w-full px-3 2xl:w-2/12">
    <label class="block tracking-wide text-left text-gray-700 text-xs font-bold mb-2">
      {{ label }}
    </label>
    <select 
       v-bind="$attrs"
       class="block appearance-none w-full h-15 bg-white text-gray-700 border border-gray-500 py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
       :value="modelValue" 
       @input="$emit('update:modelValue', $event.target.value)">
      <option></option>
      <option>New Mexico</option>
      <option>Missouri</option>
      <option>Texas</option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      default: ''
    },
    modelValue: {
      type: [String, Number, Date],
      default: ''
    }
  }
}
</script>