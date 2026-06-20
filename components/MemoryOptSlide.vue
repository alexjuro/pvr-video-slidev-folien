<template>
  <div class="memopt">
    <!-- ===== TITLE ===== -->
    <div class="memopt-title-row">
      <div class="memopt-title">Memory Optimization:</div>
      <div class="memopt-subtitle">In-Place Vectorization</div>
    </div>

    <!-- ===== CODE BLOCK ===== -->
    <pre class="slidev-code"><code class="language-java">weights^^ += learningRate * gradients^</code></pre>

    <!-- ===== STEP 1: RAM / REGISTER ===== -->
    <div v-click class="memopt-ram-wrap">
      <div class="memopt-ram">
        <div class="memopt-ram-label">weights (RAM)</div>
        <div class="memopt-cells">
          <div v-for="(v,i) in cells" :key="i" class="memopt-cell">
            <span class="memopt-cell-val">{{ v }}</span>
            <span class="memopt-cell-idx">{{ i }}</span>
          </div>
        </div>
      </div>
    </div>

    <!-- ===== STEP 2: IN-PLACE ARROWS ===== -->
    <div v-click class="memopt-arrows-wrap">
      <div class="memopt-arrows-row">
        <div v-for="(_,i) in cells" :key="i" class="memopt-arrow-cell">
          <div class="memopt-arrow-down">⬇</div>
          <div class="memopt-arrow-label">new</div>
        </div>
      </div>
    </div>

    <!-- ===== STEP 3: BOTTLENECK WARNING ===== -->
    <div v-click class="memopt-warning-wrap">
      <div class="memopt-warning">
        <div class="memopt-warn-icon">🧠</div>
        <div class="memopt-warn-text">
          <div class="memopt-warn-title">LOW MEMORY</div>
          <div class="memopt-warn-sub">ALLOCATION OVERHEAD</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const cells = ['0.25', '0.88', '0.12', '0.47', '0.03', '0.64', '0.91', '0.37']
</script>

<style scoped>
.memopt {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.8rem;
  width: 100%;
  position: relative;
}

/* ===== TITLE ===== */
.memopt-title-row {
  text-align: center;
  animation: mfadeIn 0.6s ease-out both;
}
.memopt-title {
  font-size: 2.8rem;
  font-weight: 900;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #b1c7f3;
  letter-spacing: 0.08em;
  line-height: 1.1;
}
.memopt-subtitle {
  font-size: 2rem;
  font-weight: 800;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #fea619;
  letter-spacing: 0.12em;
  margin-top: 0.1rem;
}

/* ===== RAM ===== */
.memopt-ram {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.2rem;
  padding: 0.6rem 1.2rem 0.8rem;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 12px;
}
.memopt-ram-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #fea619;
  letter-spacing: 0.12em;
  margin-bottom: 0.2rem;
}
.memopt-cells {
  display: flex;
  gap: 3px;
}
.memopt-cell {
  width: 56px;
  padding: 0.3rem 0;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 6px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.1rem;
}
.memopt-cell-val {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.85rem;
  font-weight: 700;
  color: #ffffff;
}
.memopt-cell-idx {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.45rem;
  font-weight: 600;
  color: #32476c;
}

/* ===== ARROWS ===== */
.memopt-arrows-row {
  display: flex;
  gap: 3px;
}
.memopt-arrow-cell {
  width: 56px;
  display: flex;
  flex-direction: column;
  align-items: center;
  animation: mfadeIn 0.4s ease-out both;
}
.memopt-arrow-down {
  font-size: 1rem;
  color: #009d8d;
  animation: mbounce 0.6s ease-in-out infinite alternate;
}
.memopt-arrow-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.45rem;
  font-weight: 800;
  color: #009d8d;
}

/* ===== WARNING ===== */
.memopt-warning {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  padding: 0.4rem 1rem;
  background: #2a0a0a;
  border: 2px solid #ff3333;
  border-radius: 8px;
  box-shadow: 0 0 30px rgba(255,51,51,0.3), 0 0 60px rgba(255,51,51,0.1);
  animation: mwarnPulse 1.5s ease-in-out infinite;
}
.memopt-warn-icon {
  font-size: 1.6rem;
}
.memopt-warn-text {
  display: flex;
  flex-direction: column;
}
.memopt-warn-title {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 1rem;
  font-weight: 900;
  color: #ff3333;
  letter-spacing: 0.15em;
}
.memopt-warn-sub {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.6rem;
  font-weight: 700;
  color: #ff6666;
  letter-spacing: 0.1em;
}

/* ===== KEYFRAMES ===== */
@keyframes mfadeIn {
  from { opacity: 0; transform: translateY(12px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes mwarnPulse {
  0%,100% { box-shadow: 0 0 30px rgba(255,51,51,0.3), 0 0 60px rgba(255,51,51,0.1); }
  50%     { box-shadow: 0 0 45px rgba(255,51,51,0.5), 0 0 80px rgba(255,51,51,0.2); }
}
@keyframes mbounce {
  from { transform: translateY(-2px); }
  to   { transform: translateY(4px); }
}

.slidev-code {
  font-size: 1.3rem !important;
}
</style>
