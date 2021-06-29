<template>
  <div class="calculator">
    <input
      type="text"
      name="formula"
      id="formula"
      @change="formula($event.target.value)"
      class="form-control text-center mb-3"
    />

    <p class="mb-0 calculator__result">
        <strong>Resultado:</strong>
        <span v-if="result > 0">
        {{ result }}
        </span>
    </p>
    <div v-if="history.length > 0">
        <h4 class="text-center mb-3">
            <strong>Histórico</strong>
        </h4>

        <ul class="calculator__history">
            <li
                v-for="calculation in history"
                :key="calculation.key"
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
    }
  },

  methods: {
    formula(value) {
      this.$emit("input", value);
    },
  },
};
</script>

<style>
</style>