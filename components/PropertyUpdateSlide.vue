<template>
  <div class="pup">
    <!-- ===== TITLE ===== -->
    <div class="pup-title-row">
      <div class="pup-title">Object Properties</div>
    </div>

    <!-- ===== CODE BLOCK ===== -->
    <pre class="slidev-code"><code class="language-java">layers^.bias = 0.5</code></pre>

    <!-- ===== THREE LAYER RECTANGLES ===== -->
    <div class="pup-layers">
      <!-- Step 2 trigger -->
      <div v-click="2" class="pup-step2"></div>

      <div v-click="1" class="pup-layers-inner">
        <div v-for="(layer, i) in layers" :key="i" class="pup-layer-row">
          <div class="pup-layer" :style="{ animationDelay: `${i * 0.15}s` }">
            <span class="pup-layer-label">{{ layer.name }}</span>
          </div>
          <div class="pup-conn">
            <span class="pup-conn-arrow">→</span>
          </div>
          <div class="pup-bias-box" :style="{ animationDelay: `${i * 0.1}s` }">
            <span class="pup-bias-key">bias</span>
            <span class="pup-bias-op">: </span>
            <span class="pup-bias-val">0.5</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- REFERENCE -->
  <span class="ref">[4]</span>
</template>

<script setup>
const layers = [
  { name: 'Input Layer' },
  { name: 'Hidden Layer' },
  { name: 'Output Layer' },
]
</script>

<style scoped>
.pup {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.8rem;
  width: 100%;
}

/* ===== TITLE ===== */
.pup-title-row {
  text-align: center;
  animation: pfadeIn 0.6s ease-out both;
}
.pup-title {
  font-size: 2.8rem;
  font-weight: 900;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #fea619;
  letter-spacing: 0.08em;
  line-height: 1.1;
}

/* ===== LAYERS ===== */
.pup-layers {
  position: relative;
}
.pup-step2 {
  position: absolute;
  pointer-events: none;
  opacity: 0;
  width: 0;
  height: 0;
}
.pup-layers-inner {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}
.pup-layer-row {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.pup-layer {
  display: flex;
  align-items: center;
  width: 200px;
  padding: 0.5rem 1rem;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 8px;
  opacity: 0;
  animation: pfadeIn 0.4s ease-out forwards;
}
.pup-layer-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.75rem;
  font-weight: 600;
  color: #ffffff;
}

/* ===== CONNECTION ARROW ===== */
.pup-conn {
  opacity: 0;
  animation: pfadeIn 0.3s ease-out both;
}
.pup-conn-arrow {
  font-size: 1.2rem;
  color: #009d8d;
  font-weight: 700;
}
.pup-layers:has(.pup-step2:not(.slidev-vclick-hidden)) .pup-conn {
  animation: pfadeIn 0.3s ease-out forwards;
}

/* ===== BIAS BOX ===== */
.pup-bias-box {
  display: flex;
  align-items: center;
  gap: 0.2rem;
  padding: 0.3rem 0.6rem;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 6px;
  opacity: 0;
}
.pup-layers:has(.pup-step2:not(.slidev-vclick-hidden)) .pup-bias-box {
  animation: ppopIn 0.3s ease-out forwards;
}
.pup-bias-key {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  font-weight: 600;
  color: #b1c7f3;
}
.pup-bias-op {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  color: #778cb5;
}
.pup-bias-val {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.75rem;
  font-weight: 800;
  color: #fea619;
}

/* ===== KEYFRAMES ===== */
.ref {
  position: fixed;
  bottom: 1rem;
  right: 1.5rem;
  font-size: 0.8rem;
  color: #999;
}

@keyframes pfadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes ppopIn {
  from { opacity: 0; transform: scale(0.7); }
  to   { opacity: 1; transform: scale(1); }
}

.slidev-code {
  font-size: 1.3rem !important;
}
</style>
