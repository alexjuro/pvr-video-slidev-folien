<template>
  <div class="memopt">
    <!-- ===== TITLE ===== -->
    <div class="memopt-title-row">
      <div class="memopt-title">In-Place Vectorization</div>
    </div>

    <!-- ===== CODE BLOCK ===== -->
    <pre
      class="slidev-code"
    ><code class="language-java">weights^^ += learningRate * gradients^</code></pre>

    <!-- ===== STEP 1: RAM / REGISTER ===== -->
    <div v-click class="memopt-ram-wrap">
      <div class="memopt-ram">
        <div class="memopt-ram-label">weights (RAM)</div>
        <div class="memopt-cells">
          <div v-for="(v, i) in cells" :key="i" class="memopt-cell">
            <span class="memopt-cell-val">{{ v }}</span>
            <span class="memopt-cell-idx">{{ i }}</span>
          </div>
        </div>
      </div>
    </div>

    <!-- ===== STEP 2: IN-PLACE ARROWS ===== -->
    <div v-click class="memopt-arrows-wrap">
      <div class="memopt-arrows-row">
        <div v-for="(_, i) in cells" :key="i" class="memopt-arrow-cell">
          <div class="memopt-arrow-down">▶</div>
          <div class="memopt-arrow-label">new</div>
        </div>
      </div>
    </div>

    <!-- ===== STEP 3: BOTTLENECK WARNING ===== -->
    <div v-click class="memopt-warning-wrap">
      <div class="memopt-warning">
        <div class="memopt-warn-icon">🧠</div>
        <div class="memopt-warn-text">
          <div class="memopt-warn-title">SPEICHERMANGEL</div>
          <div class="memopt-warn-sub">ALLOCATIONS-OVERHEAD</div>
        </div>
      </div>
    </div>
  </div>

  <!-- REFERENCE -->
  <span class="ref">[4]</span>
</template>

<script setup>
const cells = ["0.25", "0.88", "0.12", "0.47", "0.03", "0.64", "0.91", "0.37"];
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
}
.memopt-title {
  font-size: 2.8rem;
  font-weight: 900;
  font-family: "JetBrains Mono", "Fira Code", monospace;
  color: #b1c7f3;
  letter-spacing: 0.08em;
  line-height: 1.1;
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
  font-family: "JetBrains Mono", "Fira Code", monospace;
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
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #ffffff;
}
.memopt-cell-idx {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.45rem;
  font-weight: 700;
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
  font-size: 0.85rem;
  color: #fea619;
  line-height: 1;
  transform: rotate(90deg);
}
.memopt-arrow-label {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.45rem;
  font-weight: 800;
  color: #009d8d;
}

/* ===== WARNING ===== */
.memopt-warning {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  padding: 0.3rem 0.6rem;
  background: #2a0a0a;
  border: 2px solid #ba1a1a;
  border-radius: 8px;
}
.memopt-warn-icon {
  font-size: 1.6rem;
}
.memopt-warn-text {
  display: flex;
  flex-direction: column;
}
.memopt-warn-title {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.85rem;
  font-weight: 700;
  color: #ba1a1a;
  letter-spacing: 0.15em;
}
.memopt-warn-sub {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #ba1a1a;
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

@keyframes mfadeIn {
  from {
    opacity: 0;
    transform: translateY(12px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.slidev-code {
  font-size: 1.5rem !important;
}
</style>
