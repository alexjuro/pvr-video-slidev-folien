<template>
  <div class="ovec">
    <!-- ===== TITLE ===== -->
    <div class="ovec-title-row">
      <div class="ovec-title">Element-wise Methods</div>
    </div>

    <!-- ===== CODE BLOCK ===== -->
    <pre class="slidev-code"><code class="language-java">states = neurons^.getActiveState()</code></pre>

    <!-- ===== VISUAL ===== -->
    <div class="ovec-visual">
      <!-- Step 3 trigger (invisible, just for :has() selectors) -->
      <div v-click="3" class="ovec-step3-trigger"></div>

      <!-- ---- Left: Neurons (step 1) ---- -->
      <div v-click="1" class="ovec-col ovec-neurons">
        <div class="ovec-col-label">neurons</div>
        <div v-for="(n, i) in neurons" :key="i" class="ovec-neuron">
          <div class="ovec-neuron-ring">
            <div class="ovec-neuron-dot"></div>
          </div>
          <div class="ovec-neuron-idx">{{ n.id }}</div>
          <!-- flying value, hidden until step 3 -->
          <div class="ovec-flying-val" :style="{ animationDelay: `${i * 0.1}s` }">{{ n.val }}</div>
        </div>
      </div>

      <!-- ---- Middle: Connections (step 2) ---- -->
      <div v-click="2" class="ovec-col ovec-connections">
        <div class="ovec-col-label">&nbsp;</div>
        <div v-for="(_, i) in neurons" :key="i" class="ovec-conn-row" :style="{ animationDelay: `${i * 0.08}s` }">
          <div class="ovec-conn-line"></div>
          <div class="ovec-conn-arrow">▶</div>
        </div>
      </div>

      <!-- ---- Right: States (step 1) ---- -->
      <div v-click="1" class="ovec-col ovec-states">
        <div class="ovec-col-label">states</div>
        <div v-for="(n, i) in neurons" :key="i" class="ovec-state-row">
          <div class="ovec-state-cell">
            <span class="ovec-state-val" :style="{ animationDelay: `${i * 0.1}s` }">{{ n.val }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- REFERENCE -->
  <span class="ref">[4]</span>
</template>

<script setup>
const neurons = [
  { id: 0, val: '0.80' },
  { id: 1, val: '0.21' },
  { id: 2, val: '0.95' },
  { id: 3, val: '0.07' },
  { id: 4, val: '0.63' },
  { id: 5, val: '0.44' },
]
</script>

<style scoped>
.ovec {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.7rem;
  width: 100%;
}

/* ===== TITLE ===== */
.ovec-title-row {
  text-align: center;
  animation: ofadeIn 0.6s ease-out both;
}
.ovec-title {
  font-size: 2.8rem;
  font-weight: 900;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #b1c7f3;
  letter-spacing: 0.08em;
  line-height: 1.1;
}
.ovec-subtitle {
  font-size: 2rem;
  font-weight: 800;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #fea619;
  letter-spacing: 0.12em;
  margin-top: 0.1rem;
}

/* ===== VISUAL ===== */
.ovec-visual {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  position: relative;
}
.ovec-col {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.35rem;
}
.ovec-col-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #778cb5;
  letter-spacing: 0.1em;
  margin-bottom: 0.2rem;
  height: 1rem;
}

/* ===== STEP 3 TRIGGER ===== */
.ovec-step3-trigger {
  position: absolute;
  pointer-events: none;
  opacity: 0;
  width: 0;
  height: 0;
}

/* ===== NEURONS ===== */
.ovec-neuron {
  display: flex;
  align-items: center;
  gap: 0.3rem;
  height: 40px;
  position: relative;
}
.ovec-neuron-ring {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  border: 1.5px solid #32476c;
  background: #0b2447;
  display: flex;
  align-items: center;
  justify-content: center;
}
.ovec-neuron-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #778cb5;
}
.ovec-neuron-idx {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.45rem;
  font-weight: 700;
  color: #32476c;
  min-width: 10px;
}

/* ===== FLYING VALUES ===== */
.ovec-flying-val {
  position: absolute;
  left: 44px;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #009d8d;
  opacity: 0;
}
.ovec-visual:has(.ovec-step3-trigger:not(.slidev-vclick-hidden)) .ovec-flying-val {
  animation: oflyRight 0.5s ease-out forwards;
}

/* ===== CONNECTIONS ===== */
.ovec-connections {
  width: 60px;
}
.ovec-connections.slidev-vclick-hidden {
  display: flex !important;
  visibility: hidden;
}
.ovec-conn-row {
  display: flex;
  align-items: center;
  gap: 2px;
  height: 40px;
  opacity: 0;
  animation: ofadeIn 0.4s ease-out forwards;
}
.ovec-conn-line {
  flex: 1;
  height: 2px;
  background: linear-gradient(90deg, #fea619, #009d8d);
  border-radius: 1px;
}
.ovec-conn-arrow {
  font-size: 0.7rem;
  color: #009d8d;
  line-height: 1;
}

/* ===== STATES ===== */
.ovec-state-row {
  display: flex;
  align-items: center;
  height: 40px;
}
.ovec-state-cell {
  width: 50px;
  height: 30px;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.ovec-state-val {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #009d8d;
  opacity: 0;
}
.ovec-visual:has(.ovec-step3-trigger:not(.slidev-vclick-hidden)) .ovec-state-val {
  animation: opopIn 0.3s ease-out both;
}

/* ===== KEYFRAMES ===== */
.ref {
  position: fixed;
  bottom: 1rem;
  right: 1.5rem;
  font-size: 0.8rem;
  color: #999;
}

@keyframes ofadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes opopIn {
  from { opacity: 0; transform: scale(0.5); }
  to   { opacity: 1; transform: scale(1); }
}
@keyframes oflyRight {
  from { opacity: 0; transform: translateX(-10px); }
  60%  { opacity: 1; }
  to   { opacity: 0; transform: translateX(60px); }
}

.slidev-code {
  font-size: 1.3rem !important;
}
</style>
