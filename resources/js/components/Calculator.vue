<template>
  <div class="calculator">
    <input
      type="text"
      name="formula"
      id="formula"
      placeholder="Digite sua fórmula aqui"
      class="form-control text-center mb-3"
      :value="expression"
      @change="formula($event.target.value)"
    />

    <p class="mb-0 calculator__result">
        <strong>Resultado:</strong>
        <span v-if="result > 0" class="p-1">
        {{ result }}
        </span>
    </p>
    <div v-if="history.length > 0">
        <h4 class="text-center mb-3">
            <strong>Histórico</strong>
        </h4>

        <ul class="calculator__history">
            <li
                v-for="(calculation, index) in history"
                :key="index"
                @click="retriveHistory(index)"
                class="p-2"
            >
                {{ calculation.formula }} = {{ calculation.result }}
            </li>
        </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",

  props: {
    result: {
      type: Number,
      require: true,
    },
    history: {
        type: Array,
        require: true,
    },
    expression: {
      type: String,
      require: true,
    },
  },

  methods: {
    formula(value) {
      this.$emit('input', value)
    },
    retriveHistory(value) {
        this.$emit('retriveHistory', value)
    }
  },
};
</script>