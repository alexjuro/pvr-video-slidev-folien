<template>
  <div class="iv">
    <!-- ===== TITLE ===== -->
    <div class="iv-title-row">
      <div class="iv-title">Implicit Vectorization</div>
    </div>

    <!-- ===== STEP 1: CODE COMPARISON ===== -->
    <div v-click="1" class="iv-code-area">
      <div class="iv-scalar">
        <pre class="slidev-code"><code class="language-java">y = sin(x)</code></pre>
      </div>
      <pre class="slidev-code iv-code-main"><code class="language-java">y = sin(weights)</code></pre>
    </div>

    <!-- ===== STEP 2: ARRAY GRID ===== -->
    <div v-click="2" class="iv-array-wrap">
      <!-- Step 4 trigger for flooding -->
      <div v-click="4" class="iv-step4-trigger"></div>
      <div class="iv-array">
        <div
          v-for="(cell, i) in cells"
          :key="i"
          class="iv-cell"
          :style="{ transitionDelay: `${i * 0.06}s` }"
        >
          <span class="iv-cell-val iv-cell-before">{{ cell.before }}</span>
          <span class="iv-cell-val iv-cell-after">{{ cell.after }}</span>
        </div>
      </div>
    </div>

    <!-- ===== STEP 3: TRANSPILE LINE ===== -->
    <div v-click="3" class="iv-transpile">
      <pre class="slidev-code iv-code-main"><code class="language-java">y = sin(weights^)</code></pre>
      <div class="iv-transpile-label">Compiler transpiliert zu:</div>
    </div>
  </div>

  <!-- REFERENCE -->
  <span class="ref">[4]</span>
</template>

<script setup>
const raw = [0.10, 0.35, 0.60, 0.85, 0.95, 0.80, 0.50, 0.20, 0.02, 0.15, 0.45, 0.70, 0.90, 0.88, 0.65, 0.30]
const cells = raw.map((v, i) => ({
  before: v.toFixed(2),
  after: Math.sin(v * Math.PI).toFixed(2),
}))
</script>

<style scoped>
.iv {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 1.2rem;
  width: 100%;
}

/* ===== TITLE ===== */
.iv-title-row {
  text-align: center;
  animation: ivfadeIn 0.6s ease-out both;
}
.iv-title {
  font-size: 2.8rem;
  font-weight: 900;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #b1c7f3;
  letter-spacing: 0.08em;
  line-height: 1.1;
}

/* ===== CODE ===== */
.iv-code-area {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  animation: ivfadeIn 0.5s ease-out both;
}
.iv-scalar {
  opacity: 0.4;
}

/* ===== STEP 4 TRIGGER ===== */
.iv-step4-trigger {
  position: absolute;
  pointer-events: none;
  opacity: 0;
  width: 0;
  height: 0;
}

/* ===== ARRAY ===== */
.iv-array-wrap {
  position: relative;
}
.iv-array {
  display: grid;
  grid-template-columns: repeat(8, 34px);
  gap: 2px;
  padding: 0.3rem;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 8px;
  animation: ivfadeIn 0.5s ease-out both;
  transition: border-color 0.6s;
}
.iv-array-wrap:has(.iv-step4-trigger:not(.slidev-vclick-hidden)) .iv-array {
  border-color: #009d8d;
}
.iv-cell {
  height: 26px;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 3px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.4s, border-color 0.4s;
  position: relative;
}
.iv-array-wrap:has(.iv-step4-trigger:not(.slidev-vclick-hidden)) .iv-cell {
  background: #00120f;
  border-color: #009d8d;
}
.iv-cell-val {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.5rem;
  font-weight: 700;
  color: #ffffff;
}
.iv-cell-after {
  display: none;
}
.iv-array-wrap:has(.iv-step4-trigger:not(.slidev-vclick-hidden)) .iv-cell-before {
  display: none;
}
.iv-array-wrap:has(.iv-step4-trigger:not(.slidev-vclick-hidden)) .iv-cell-after {
  display: inline;
  color: #009d8d;
}

/* ===== TRANSPILE ===== */
.iv-transpile {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  animation: ivfadeIn 0.5s ease-out both;
}
.iv-transpile-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #74777f;
  letter-spacing: 0.1em;
}

/* ===== KEYFRAMES ===== */
.ref {
  position: fixed;
  bottom: 1rem;
  right: 1.5rem;
  font-size: 0.8rem;
  color: #999;
}

@keyframes ivfadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}
.slidev-code {
  font-size: 1.3rem !important;
}
</style>
