<template>
  <div v-html="html" class="codeblock-wrap"></div>
</template>

<script setup>
import { ref, onMounted, watch } from 'vue'
import { createHighlighter } from 'shiki'

const props = defineProps({
  code: { type: String, required: true },
  lang: { type: String, default: 'java' },
})

const html = ref('')
let highlighter = null

async function highlight() {
  if (!highlighter) {
    highlighter = await createHighlighter({
      langs: [props.lang],
      themes: ['vitesse-dark'],
    })
  }
  html.value = highlighter.codeToHtml(props.code, {
    lang: props.lang,
    theme: 'vitesse-dark',
  })
}

onMounted(highlight)
watch(() => props.code, highlight)
</script>

<style scoped>
.codeblock-wrap {
  display: contents;
}
.codeblock-wrap :deep(pre) {
  display: block;
  overflow-x: auto;
  margin: 0;
  font-family: var(--slidev-code-font-family, 'PT Mono', monospace) !important;
  font-size: 1.5rem !important;
  line-height: var(--slidev-code-line-height, 1.7) !important;
  padding: var(--slidev-code-padding, 0.3rem 0.6rem) !important;
  border-radius: var(--slidev-code-radius, 4px) !important;
}
.codeblock-wrap :deep(code) {
  font-family: inherit;
}
</style>
