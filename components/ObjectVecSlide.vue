<template>
  <div class="ovec">
    <!-- ===== TITLE ===== -->
    <div class="ovec-title-row">
      <div class="ovec-title">Object Vectorization:</div>
      <div class="ovec-subtitle">Element-wise Methods</div>
    </div>

    <!-- ===== CODE BLOCK ===== -->
    <div class="ovec-code-wrap">
      <pre class="ovec-code"><code><span class="ov-var">states</span><span class="ov-op"> = </span><span class="ov-var">neurons</span><span class="ov-hat">^</span><span class="ov-meth">getActiveState</span><span class="ov-op">()</span></code></pre>
    </div>

    <!-- ===== VISUAL ===== -->
    <div class="ovec-visual">
      <!-- ---- Left: Neuron column ---- -->
      <div class="ovec-neurons">
        <div class="ovec-neuron-col-label">neurons</div>
        <div
          v-for="(n, i) in neurons"
          :key="i"
          class="ovec-neuron"
          :class="{ 'ovec-neuron-lit': phase >= 3 }"
          :style="{ animationDelay: `${3.2 + i * 0.1}s` }"
        >
          <div class="ovec-neuron-ring">
            <div class="ovec-neuron-dot"></div>
          </div>
          <div class="ovec-neuron-idx">{{ n.id }}</div>
          <!-- flying value -->
          <Transition name="ovec-fly">
            <div v-if="phase >= 3" class="ovec-flying-val" :style="{ animationDelay: `${3.5 + i * 0.12}s` }">
              {{ n.val }}
            </div>
          </Transition>
        </div>
      </div>

      <!-- ---- Middle: broadcast wave (Phase 2) ---- -->
      <div v-if="phase >= 2" class="ovec-wave-zone">
        <div class="ovec-wave-line"></div>
        <div class="ovec-wave-label">broadcast</div>
      </div>

      <!-- ---- Right: states array ---- -->
      <div class="ovec-states" :class="{ 'ovec-states-fill': phase >= 3 }">
        <div class="ovec-states-col-label">states</div>
        <div
          v-for="(n, i) in neurons"
          :key="i"
          class="ovec-state-cell"
          :class="{ 'ovec-state-filled': phase >= 3 }"
          :style="{ transitionDelay: `${3.5 + i * 0.12}s` }"
        >
          <span v-if="phase >= 3" class="ovec-state-val">{{ n.val }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const phase = ref(0)

const neurons = [
  { id: 0, val: '0.80' },
  { id: 1, val: '0.21' },
  { id: 2, val: '0.95' },
  { id: 3, val: '0.07' },
  { id: 4, val: '0.63' },
  { id: 5, val: '0.44' },
]

onMounted(() => {
  // phase 0→1 after 1.0s: ^ blinks
  setTimeout(() => { phase.value = 1 }, 1000)
  // phase 1→2 after 2.5s: broadcast wave
  setTimeout(() => { phase.value = 2 }, 3500)
  // phase 2→3 after 2.0s: neuron + fill
  setTimeout(() => { phase.value = 3 }, 5500)
})
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
  color: #00e5ff;
  text-shadow: 0 0 40px rgba(0,229,255,0.5), 0 0 80px rgba(0,229,255,0.2);
  letter-spacing: 0.08em;
  line-height: 1.1;
}
.ovec-subtitle {
  font-size: 2rem;
  font-weight:800;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #ffa500;
  text-shadow: 0 0 30px rgba(255,165,0,0.4);
  letter-spacing: 0.12em;
  margin-top: 0.1rem;
}

/* ===== CODE ===== */
.ovec-code-wrap {
  padding: 0.3rem 1rem;
  background: #1a1a2e;
  border: 2px solid #0f3460;
  border-radius: 8px;
  opacity: 0;
  animation: ofadeIn 0.6s ease-out 0.3s both;
}
.ovec-code {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 1.2rem;
  font-weight: 600;
  margin: 0;
}
.ov-var { color: #ffd700; }
.ov-op  { color: #7ec8e3; }
.ov-meth { color: #7ec8e3; }
.ov-hat {
  font-size: 1.4rem;
  font-weight: 900;
  color: #ff6bff;
  text-shadow: 0 0 20px rgba(255,107,255,0.8), 0 0 40px rgba(255,107,255,0.4);
  animation: ohatPulse 1.2s ease-in-out 1.0s infinite both;
}

/* ===== VISUAL ===== */
.ovec-visual {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  opacity: 0;
  animation: ofadeIn 0.6s ease-out 0.6s both;
}

/* ---- Neurons column ---- */
.ovec-neurons {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.35rem;
}
.ovec-neuron-col-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.55rem;
  font-weight: 700;
  color: #5a7a9a;
  letter-spacing: 0.1em;
  margin-bottom: 0.2rem;
}
.ovec-neuron {
  display: flex;
  align-items: center;
  gap: 0.3rem;
  position: relative;
  transition: transform 0.4s, filter 0.4s;
}
.ovec-neuron-lit {
  transform: scale(1.05);
  filter: brightness(1.3);
}
.ovec-neuron-ring {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  border: 2px solid #0f3460;
  background: #0a0a1a;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: border-color 0.5s, background 0.5s, box-shadow 0.5s;
}
.ovec-neuron-lit .ovec-neuron-ring {
  border-color: #ff6bff;
  background: #1a0a1a;
  box-shadow: 0 0 15px rgba(255,107,255,0.25);
}
.ovec-neuron-dot {
  width: 8px;
  height: 8px;
  border-radius:50%;
  background: #5a7a9a;
  transition: background 0.5s;
}
.ovec-neuron-lit .ovec-neuron-dot {
  background: #ff6bff;
  box-shadow: 0 0 10px rgba(255,107,255,0.5);
}
.ovec-neuron-idx {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.45rem;
  font-weight: 600;
  color: #3a5a7a;
  min-width: 10px;
}

/* flying value */
.ovec-flying-val {
  position: absolute;
  left: 44px;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.6rem;
  font-weight: 700;
  color: #39ff14;
  text-shadow: 0 0 8px rgba(57,255,20,0.6);
  animation: oflyRight 0.5s ease-out forwards;
}

/* ---- Wave zone ---- */
.ovec-wave-zone {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.2rem;
}
.ovec-wave-line {
  width: 40px;
  height: 2px;
  background: linear-gradient(90deg, #ff6bff, #39ff14);
  position: relative;
  animation: owaveExpand 0.8s ease-out 3.5s both;
}
.ovec-wave-line::before,
.ovec-wave-line::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 2px;
  background: inherit;
  top: -4px;
  opacity: 0.4;
  animation: owaveExpand 0.8s ease-out 3.7s both;
}
.ovec-wave-line::after {
  top: 4px;
  animation-delay: 3.9s;
}
.ovec-wave-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.45rem;
  font-weight: 700;
  color: #ff6bff;
  letter-spacing: 0.1em;
  opacity: 0;
  animation: ofadeIn 0.4s ease-out 4.0s both;
}

/* ---- States column ---- */
.ovec-states {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.35rem;
}
.ovec-states-col-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.55rem;
  font-weight: 700;
  color: #5a7a9a;
  letter-spacing: 0.1em;
  margin-bottom: 0.2rem;
}
.ovec-state-cell {
  width: 50px;
  height: 30px;
  background: #0a0a1a;
  border: 2px solid #0f3460;
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: border-color 0.5s, background 0.5s, box-shadow 0.5s;
}
.ovec-state-filled {
  border-color: #39ff14;
  background: #0a1a0a;
  box-shadow: 0 0 12px rgba(57,255,20,0.2);
}
.ovec-state-val {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  font-weight: 700;
  color: #39ff14;
  text-shadow: 0 0 8px rgba(57,255,20,0.4);
  animation: opopIn 0.3s ease-out both;
}

/* ===== TRANSITIONS ===== */
.ovec-fly-enter-active {
  animation: oflyRight 0.5s ease-out;
}
.ovec-fly-leave-active {
  animation: oflyRight 0.3s ease-in reverse;
}

/* ===== KEYFRAMES ===== */
@keyframes ofadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes opopIn {
  from { opacity: 0; transform: scale(0.5); }
  to   { opacity: 1; transform: scale(1); }
}
@keyframes ohatPulse {
  0%,100% { opacity: 1; transform: scale(1); }
  50%     { opacity: 0.6; transform: scale(1.3); }
}
@keyframes oflyRight {
  from { opacity: 0; transform: translateX(-10px); }
  to   { opacity: 1; transform: translateX(60px); }
}
@keyframes owaveExpand {
  from { transform: scaleX(0); opacity: 0; }
  to   { transform: scaleX(1); opacity: 1; }
}
</style>
