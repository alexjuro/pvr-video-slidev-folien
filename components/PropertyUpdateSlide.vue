<template>
  <div class="pup">
    <!-- ===== TITLE ===== -->
    <div class="pup-title-row">
      <div class="pup-title">No Boilerplate:</div>
      <div class="pup-subtitle">Object Properties</div>
    </div>

    <!-- ===== CODE BLOCK ===== -->
    <div class="pup-code-wrap">
      <pre class="pup-code"><code><span class="pp-var">layers</span><span class="pp-hat">^</span><span class="pp-prop">bias</span><span class="pp-op"> = </span><span class="pp-val">0.5</span></code></pre>
    </div>

    <!-- ===== THREE LAYER RECTANGLES ===== -->
    <div v-if="phase >= 2" class="pup-layers">
      <div
        v-for="(layer, i) in layers"
        :key="i"
        class="pup-layer"
        :class="{ 'pup-layer-lit': phase >= 3 }"
        :style="{ animationDelay: `${2.0 + i * 0.2}s` }"
      >
        <div class="pup-layer-label">{{ layer.name }}</div>
        <Transition name="pup-fade">
          <div v-if="phase >= 3" class="pup-layer-bias">
            <span class="pup-bias-key">bias</span><span class="pup-bias-op">: </span><span class="pup-bias-val">0.5</span>
          </div>
        </Transition>
      </div>

      <!-- broadcast beam from ^ -->
      <div v-if="phase >= 3" class="pup-beam-zone">
        <div class="pup-beam-arrow-left">&nbsp;</div>
        <div class="pup-beam-line"></div>
        <div class="pup-beam-arrow">⬇</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const phase = ref(0)

const layers = [
  { name: 'Input Layer' },
  { name: 'Hidden Layer' },
  { name: 'Output Layer' },
]

onMounted(() => {
  // phase 0→1 after 0.8s: code is visible, 0.5 blinks
  setTimeout(() => { phase.value = 1 }, 800)
  // phase 1→2 after 2.0s: three layer rects appear
  setTimeout(() => { phase.value = 2 }, 2800)
  // phase 2→3 after 2.0s: beam + bias values
  setTimeout(() => { phase.value = 3 }, 4800)
})
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
  color: #00e5ff;
  text-shadow: 0 0 40px rgba(0,229,255,0.5), 0 0 80px rgba(0,229,255,0.2);
  letter-spacing: 0.08em;
  line-height: 1.1;
}
.pup-subtitle {
  font-size: 2rem;
  font-weight: 800;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #ffa500;
  text-shadow: 0 0 30px rgba(255,165,0,0.4);
  letter-spacing: 0.12em;
  margin-top: 0.1rem;
}

/* ===== CODE ===== */
.pup-code-wrap {
  padding: 0.4rem 1.2rem;
  background: #1a1a2e;
  border: 2px solid #0f3460;
  border-radius: 8px;
  opacity: 0;
  animation: pfadeIn 0.6s ease-out 0.3s both;
}
.pup-code {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 1.2rem;
  font-weight: 600;
  margin: 0;
}
.pp-var { color: #ffd700; }
.pp-hat {
  font-size: 1.4rem;
  font-weight: 900;
  color: #39ff14;
  text-shadow: 0 0 20px rgba(57,255,20,0.8), 0 0 40px rgba(57,255,20,0.4);
  animation: phatPulse 1.2s ease-in-out 0.8s infinite both;
}
.pp-prop { color: #7ec8e3; }
.pp-op   { color: #7ec8e3; }
.pp-val {
  color: #ffd700;
  animation: pvalBlink 0.7s ease-in-out 0.8s 4 both;
}

/* ===== LAYERS ===== */
.pup-layers {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.4rem;
  position: relative;
}
.pup-layer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 340px;
  padding: 0.5rem 1rem;
  background: linear-gradient(145deg,#1a1a2e,#16213e);
  border: 2px solid #0f3460;
  border-radius: 8px;
  opacity: 0;
  animation: pfadeIn 0.5s ease-out both;
  transition: border-color 0.5s, background 0.5s, box-shadow 0.5s;
}
.pup-layer-lit {
  border-color: #39ff14;
  background: linear-gradient(145deg,#1a2a1e,#16213e);
  box-shadow: 0 0 20px rgba(57,255,20,0.15);
}
.pup-layer-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.75rem;
  font-weight: 600;
  color: #ccc;
}
.pup-layer-bias {
  display: flex;
  align-items: center;
  gap: 0.2rem;
}
.pup-bias-key {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  font-weight: 600;
  color: #7ec8e3;
}
.pup-bias-op {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  color: #5a7a9a;
}
.pup-bias-val {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.75rem;
  font-weight: 800;
  color: #ffd700;
  text-shadow: 0 0 10px rgba(255,215,0,0.4);
}

/* ===== BEAM ===== */
.pup-beam-zone {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.15rem;
  position: absolute;
  left: -50px;
  top: 50%;
  transform: translateY(-50%);
}
.pup-beam-line {
  width: 2px;
  height: 100px;
  background: linear-gradient(180deg, #39ff14, transparent);
  animation: pbeamFade 0.8s ease-out both;
}
.pup-beam-arrow {
  font-size: 1rem;
  color: #39ff14;
  text-shadow: 0 0 12px rgba(57,255,20,0.6);
  animation: pbeamBounce 0.5s ease-in-out infinite alternate;
}

/* ===== TRANSITIONS ===== */
.pup-fade-enter-active {
  transition: opacity 0.4s, transform 0.4s;
}
.pup-fade-leave-active {
  transition: opacity 0.3s;
}
.pup-fade-enter-from {
  opacity: 0;
  transform: scale(0.8);
}
.pup-fade-leave-to {
  opacity: 0;
}

/* ===== KEYFRAMES ===== */
@keyframes pfadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes phatPulse {
  0%,100% { opacity: 1; transform: scale(1); }
  50%     { opacity: 0.7; transform: scale(1.25); }
}
@keyframes pvalBlink {
  0%,100% { opacity: 1; color: #ffd700; }
  50%     { opacity: 1; color: #ffff00; text-shadow: 0 0 15px rgba(255,255,0,0.6); }
}
@keyframes pbeamFade {
  from { opacity: 0; }
  to   { opacity: 1; }
}
@keyframes pbeamBounce {
  from { transform: translateY(0); }
  to   { transform: translateY(4px); }
}
</style>
