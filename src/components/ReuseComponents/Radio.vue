<template>
    <div>
        <div class="flex items-center mb-4">
            <input 
            id="default-radio-1" 
            type="radio" 
            name="default-radio"
            :value="modelValue"
            @input="$emit('update:modelValue', $event.target.value)" 
            class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 focus:ring-blue-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600" />
            <label for="default-radio-1" class="ml-2 text-sm font-bold text-gray-900 dark:text-gray-300">{{ label }}</label>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        label: {
            type: String,
            default: ''
        },
        label1: {
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
