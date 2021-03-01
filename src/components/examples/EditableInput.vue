<template>
  <card title="Input editable for user">
    <date-picker
      v-model="date"
      format="jYYYY/jMM/jDD"
      placeholder="YYYY/MM/DD"
      :editable="true"
      @input="codeOutput"
    />
    <code v-if="output" class="code">{{ output.value[0] }}</code>
    <template v-slot:code>
      <!-- eslint-disable -->
      <pre v-highlightjs><code class="css" v-pre>input.is-editable {
  direction: ltr;
  text-align: left;
}</code></pre>
      <pre v-highlightjs><code class="html" v-pre>&lt;date-picker
  v-model="date"
  format="jYYYY/jMM/jDD"
  placeholder="YYYY/MM/DD"
  :editable="true"
/&gt;</code></pre>
      <!-- eslint-enable -->
    </template>
  </card>
</template>

<script>
import {ref} from 'vue'
export default {
  setup() {
    const date = ref(null)
    const output = ref(null)
    const codeOutput = function (val) {
      output.value = val
    }

    return {
      date,
      output,
      codeOutput,
    }
  },
}
</script>
