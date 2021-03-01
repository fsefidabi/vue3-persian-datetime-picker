<template>
  <div>
    <h5 class="text-danger text-bold my-5">
      NOTE: Range feature is only supported for `date` type
    </h5>

    <card title="Range select" version="2.5.0">
      <date-picker
        range
        clearable
        format="YYYY-MM-DD"
        display-format="jMMMM jD"
        @input="codeOutput"
      />
      <br />
      <code v-if="output" class="code">{{ output.value }}</code>
      <template v-slot:code>
        <!-- eslint-disable -->
        <pre v-highlightjs><code class="html" v-pre>&lt;date-picker
  v-model="range"
  range
  clearable
  format="YYYY-MM-DD"
  display-format="jMMMM jD"
/&gt;</code></pre>
          <pre v-highlightjs><code class="javascript" v-pre>data() {
  return {
    range: []
  }
}</code></pre>
        <!-- eslint-enable -->
      </template>
    </card>

    <card title="With start and end time">
      <date-picker
        range
        clearable
        auto-submit
        locale="en,fa"
        min="2021-01-05"
        max="2021-02-20"
        format="YYYY-MM-DD HH:mm"
        display-format="jYYYY/jM/jD"
        @input="codeOutput"
      />
      <br />
      <code v-if="output2" class="code">{{ output2.value }}</code>
      <template v-slot:code>
        <!-- eslint-disable -->
        <pre v-highlightjs><code class="html" v-pre>&lt;date-picker
  range
  clearable
  auto-submit
  locale="en,fa"
  min="2021-02-05"
  max="2021-02-20"
  format="YYYY-MM-DD HH:mm"
  display-format="jYYYY/jM/jD"
/&gt;</code></pre>
        <pre v-highlightjs><code class="javascript" v-pre>data() {
   return {
    range: []
  }
}</code></pre>
        <!-- eslint-enable -->
      </template>
    </card>
  </div>
</template>

<script>
import {ref} from 'vue'

export default {
  setup() {
    const dates = ref('')
    const output = ref([])
    const output2 = ref([])
    const codeOutput = function (val) {
      if (output) output.value = val
      if (output2) output2.value = val
    }
    return {
      dates,
      output,
      output2,
      codeOutput
    }
  }
}
</script>
