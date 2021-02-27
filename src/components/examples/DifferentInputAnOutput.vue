<template>
  <card title="Different input and output values">
    <date-picker
      value="date"
      input-format="YYYY-MM-DD"
      format="jYYYY/jMM/jDD"
      @input="codeOutput"
    />
    <code class="code" v-if="output">{{ date }}</code>

    <template v-slot:code>
      <!-- eslint-disable -->
      <pre v-highlightjs><code class="html" v-pre>&lt;date-picker
  value="2017-05-10"
  input-format="YYYY-MM-DD"
  format="jYYYY/jMM/jDD"
  @input="date=$event"
/&gt;</code></pre>
      <!-- eslint-enable -->
    </template>

    <template v-slot:docs>
      <!-- eslint-disable -->
      <pre v-highlightjs><code class="javascript" v-pre>
        /**
        * Different input and output format
        * 1_ set input by          value="..."
        * 2_ set input format by   input-format="..."
        * 3_ set output format by  format="..."
        * 4_ get output by         @input="date=$event"
        */
        "$event"
        type: String
        returns formatted datetime
      </code></pre>
      <pre v-highlightjs><code class="html" v-pre>
        &lt;date-picker
          value="2017/10/03"
          input-format="YYYY/MM/DD"
          format="jYYYY/jMM/jDD"
          @input="date=$event"
        /&gt;
        &lt;date-picker
          value="1396-05-05"
          input-format="jYYYY-jMM-jDD"
          format="YYYY/MM/jDD"
          @input="date=$event"
        /&gt;
      </code></pre>
      <!-- eslint-enable -->
    </template>
  </card>
</template>

<script>
import { ref } from "vue";

export default {
  setup(){
    const date = '2017-05-10'
    const output = ref(null)
    const codeOutput = function (val) {
      output.value = val
    }

    return{
      date,
      output,
      codeOutput
    }
  }
}
</script>
