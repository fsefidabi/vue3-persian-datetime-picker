<template>
  <card title="Minimum and maximum">
    <date-picker
      v-model="date"
      min="1399/08/03"
      max="1399/12/14"
      format="jYYYY/jMM/jDD"
      @input="codeOutput"
    />
    <code v-if="output" class="code">{{ output.value[0] }}</code>

    <template v-slot:code>
      <!-- eslint-disable -->
      <pre v-highlightjs><code class="html">&lt;date-picker
  v-model="date"
  min="1399/08/03"
  max="1399/12/14"
/&gt;</code></pre>
      <!-- eslint-enable -->
    </template>

    <template v-slot:docs>
      <!-- eslint-disable -->
      <pre v-highlightjs><code class="javascript">
        /**
         * Limit datetime picker minimum and maximum
         */
        "min"
        type: String
        default: Null
        example:
          20:20             //for time
          1399/12/03 20:20  //for datetime
          1399/12/14        //for date
        /*******************************/
        "max"
        type: String
        default: Null
        example: same as "min"
      </code></pre>
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
