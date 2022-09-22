<template>
   <div class="w-full 2xl:w-2/12 px-3">
        <label class="block tracking-wide text-left  text-gray-700 text-xs font-bold mb-2">
            {{ label }}
        </label>
        <input 
           v-bind="$attrs"
           class="appearance-none block w-full h-15 bg-white text-gray-700 border border-gray-500 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
           :value="modelValue" 
           type="date" 
           @input="$emit('update:modelValue', $event.target.value)" />
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