<template>
  <div class="container">
      <div class="row">
          <div class="col-12">
              <div class="card">
                    <div class="card-header text-center">
                        <h3>Calculator</h3>
                    </div>

                    <div class="card-body">
                        <calculator-component v-model="formula"></calculator-component>
                    </div>
                </div>
          </div>
      </div>
  </div>
</template>

<script>
    export default {
        data() {
            return {
                formula: '',
                result: 0,
            }
        },

        watch: {
            formula: function(value) {
                this.calculate(value)
            }
        },
        
        methods: {
            calculate(formula) {
                console.log(math.evaluate(formula))
            }
        }
    }
</script>

<style>

</style>
Calculator