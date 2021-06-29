<template>
  <div class="container">
      <div class="row">
          <div class="col-12">
              <div class="card">
                    <div class="card-header text-center">
                        <h3>Calculadora</h3>
                    </div>

                    <div class="card-body">
                        <calculator-component
                            v-model="formula"
                            :result="result"
                            :history="history"
                            @retriveHistory="addResultToFormula"
                        >
                        </calculator-component>
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
                history: []
            }
        },

        watch: {
            formula: function(value) {
                this.calculate(value)
            }
        },
        
        methods: {
            calculate(formula) {
                this.result = math.evaluate(formula)
                this.addToHisotry(formula, this.result)
            },
            addToHisotry(formula, result) {
                const obj = {
                    formula: formula,
                    result: result
                }

                this.history.push(obj)
            },
            addResultToFormula(key) {
                console.log(key)
            }
        }
    }
</script>

<style>

</style>
Calculator