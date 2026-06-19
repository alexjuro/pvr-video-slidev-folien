<template>
  <div class="pup">
    <!-- ===== TITLE ===== -->
    <div class="pup-title-row">
      <div class="pup-title">No Boilerplate:</div>
      <div class="pup-subtitle">Object Properties</div>
    </div>

    <!-- ===== CODE BLOCK ===== -->
    <pre class="slidev-code"><code class="language-java">layers^.bias = 0.5</code></pre>

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
  color: #b1c7f3;
  letter-spacing: 0.08em;
  line-height: 1.1;
}
.pup-subtitle {
  font-size: 2rem;
  font-weight: 800;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #fea619;
  letter-spacing: 0.12em;
  margin-top: 0.1rem;
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
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 8px;
  opacity: 0;
  animation: pfadeIn 0.5s ease-out both;
  transition: border-color 0.5s, background 0.5s;
}
.pup-layer-lit {
  border-color: #009d8d;
  background: #0b2447;
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
  background: linear-gradient(180deg, #009d8d, transparent);
  animation: pbeamFade 0.8s ease-out both;
}
.pup-beam-arrow {
  font-size: 1rem;
  color: #009d8d;
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
@keyframes pbeamFade {
  from { opacity: 0; }
  to   { opacity: 1; }
}
@keyframes pbeamBounce {
  from { transform: translateY(0); }
  to   { transform: translateY(4px); }
}

.slidev-code {
  font-size: 1.3rem !important;
}
</style>
