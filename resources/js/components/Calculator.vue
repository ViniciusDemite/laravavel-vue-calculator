<template>
  <div class="calculator">
      <input type="text" name="formula" id="formula" class="form-control text-center calculator__formula" @change="formula($event.target.value)" />

      <div class="calculator__result" v-if="result > 0">{{ result }}</div>

      <div class="calculator__history"></div>
  </div>
</template>

<script>
    export default {
        name: 'Calculator',

        props: {
            result: {
                type: Float64Array,
                require: true,
            }
        },

        methods: {
            formula(value) {
                this.$emit('input', value)
            }
        }
    }
</script>

<style>

</style>