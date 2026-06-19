<template>
  <div class="hscale">
    <!-- ===== TITLE ===== -->
    <div class="hscale-title-row">
      <div class="hscale-title">Hardware-Agnostic</div>
      <div class="hscale-subtitle">Scaling</div>
    </div>

    <!-- ===== CODE ===== -->
    <pre class="slidev-code"><code class="language-java">y = sin(weights^)</code></pre>

    <!-- ===== HARDWARE SWITCH ===== -->
    <div class="hscale-switch-area">
      <!-- label -->
      <div class="hscale-switch-label">
        <span class="hscale-switch-icon">⚡</span> DEPLOYMENT TARGET
      </div>

      <!-- three options -->
      <div class="hscale-options">
        <!-- CPU -->
        <div
          class="hscale-option"
          :class="{ 'hscale-option-active': activeTarget === 'cpu' }"
          @click="switchTo('cpu')"
        >
          <div class="hscale-option-icon">
            <svg viewBox="0 0 40 40" width="32" height="32">
              <rect x="4" y="4" width="32" height="32" rx="4" fill="none" stroke="currentColor" stroke-width="2"/>
              <rect x="12" y="12" width="16" height="16" rx="1" fill="none" stroke="currentColor" stroke-width="1.2"/>
              <line x1="20" y1="4" x2="20" y2="0" stroke="currentColor" stroke-width="1.5"/>
              <line x1="20" y1="40" x2="20" y2="36" stroke="currentColor" stroke-width="1.5"/>
              <line x1="4" y1="20" x2="0" y2="20" stroke="currentColor" stroke-width="1.5"/>
              <line x1="40" y1="20" x2="36" y2="20" stroke="currentColor" stroke-width="1.5"/>
            </svg>
          </div>
          <div class="hscale-option-name">CPU</div>
          <div class="hscale-option-desc">Single Core</div>
        </div>

        <!-- GPU -->
        <div
          class="hscale-option"
          :class="{ 'hscale-option-active': activeTarget === 'gpu' }"
          @click="switchTo('gpu')"
        >
          <div class="hscale-option-icon">
            <svg viewBox="0 0 50 34" width="40" height="28">
              <rect x="2" y="2" width="46" height="30" rx="3" fill="none" stroke="currentColor" stroke-width="2"/>
              <rect x="14" y="8" width="26" height="18" rx="1" fill="none" stroke="currentColor" stroke-width="1"/>
              <rect x="4" y="10" width="6" height="14" rx="1" fill="none" stroke="currentColor" stroke-width="1"/>
              <line x1="25" y1="2" x2="25" y2="0" stroke="currentColor" stroke-width="1.2"/>
            </svg>
          </div>
          <div class="hscale-option-name">GPU</div>
          <div class="hscale-option-desc">Massive Parallel</div>
        </div>

        <!-- Cloud -->
        <div
          class="hscale-option"
          :class="{ 'hscale-option-active': activeTarget === 'cloud' }"
          @click="switchTo('cloud')"
        >
          <div class="hscale-option-icon">
            <svg viewBox="0 0 44 30" width="36" height="26">
              <!-- three server racks -->
              <rect x="2" y="2" width="12" height="26" rx="2" fill="none" stroke="currentColor" stroke-width="1.5"/>
              <rect x="4" y="5" width="8" height="3" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.8"/>
              <rect x="4" y="11" width="8" height="3" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.8"/>
              <rect x="4" y="17" width="8" height="3" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.8"/>
              <rect x="16" y="2" width="12" height="26" rx="2" fill="none" stroke="currentColor" stroke-width="1.5"/>
              <rect x="18" y="5" width="8" height="3" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.8"/>
              <rect x="18" y="11" width="8" height="3" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.8"/>
              <rect x="18" y="17" width="8" height="3" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.8"/>
              <rect x="30" y="2" width="12" height="26" rx="2" fill="none" stroke="currentColor" stroke-width="1.5"/>
              <rect x="32" y="5" width="8" height="3" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.8"/>
              <rect x="32" y="11" width="8" height="3" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.8"/>
              <rect x="32" y="17" width="8" height="3" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.8"/>
              <!-- connecting lines -->
              <line x1="14" y1="15" x2="16" y2="15" stroke="currentColor" stroke-width="1"/>
              <line x1="28" y1="15" x2="30" y2="15" stroke="currentColor" stroke-width="1"/>
            </svg>
          </div>
          <div class="hscale-option-name">Cloud</div>
          <div class="hscale-option-desc">Distributed Cluster</div>
        </div>
      </div>

      <!-- switch indicator bar -->
      <div class="hscale-switch-bar">
        <div class="hscale-switch-track">
          <div
            class="hscale-switch-thumb"
            :class="`hscale-thumb-${activeTarget}`"
          ></div>
        </div>
      </div>
    </div>

    <!-- ===== DATA FLOW VIS ===== -->
    <div class="hscale-vis">
      <Transition name="hscale-fade" mode="out-in">
        <!-- CPU: thin grid, few data points -->
        <div v-if="activeTarget === 'cpu'" key="cpu" class="hscale-vis-panel">
          <div class="hscale-vis-label">Sequential Processing</div>
          <div class="hscale-cpu-grid">
            <div v-for="i in 8" :key="i" class="hscale-cpu-core">
              <div class="hscale-core-dot"></div>
            </div>
          </div>
          <div class="hscale-flow-row">
            <span class="hscale-flow-dot" v-for="i in 4" :key="i"></span>
          </div>
        </div>

        <!-- GPU: wide grid, massive parallel -->
        <div v-else-if="activeTarget === 'gpu'" key="gpu" class="hscale-vis-panel">
          <div class="hscale-vis-label">Massive Parallel</div>
          <div class="hscale-gpu-grid">
            <div v-for="i in 32" :key="i" class="hscale-gpu-core">
              <div class="hscale-core-dot"></div>
            </div>
          </div>
          <div class="hscale-flow-row hscale-flow-wide">
            <span class="hscale-flow-dot" v-for="i in 12" :key="i"></span>
          </div>
        </div>

        <!-- Cloud: distributed cluster -->
        <div v-else key="cloud" class="hscale-vis-panel">
          <div class="hscale-vis-label">Distributed Cluster</div>
          <div class="hscale-cloud-cluster">
            <div v-for="i in 3" :key="i" class="hscale-cloud-node">
              <div class="hscale-node-box">
                <div class="hscale-node-row" v-for="j in 3" :key="j"></div>
              </div>
              <div class="hscale-node-conn"></div>
            </div>
          </div>
          <div class="hscale-flow-row hscale-flow-cloud">
            <span class="hscale-flow-dot" v-for="i in 6" :key="i"></span>
          </div>
        </div>
      </Transition>
    </div>

    <!-- ===== WRITE ONCE LABEL ===== -->
    <div class="hscale-motto">
      <span class="hscale-motto-line">Write once,</span>
      <span class="hscale-motto-em">scale anywhere</span>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const activeTarget = ref('cpu')
const step = ref(0)

function switchTo(target) {
  activeTarget.value = target
}

onMounted(() => {
  // auto-animate through the three targets
  setTimeout(() => { step.value = 1 }, 2000)
  setTimeout(() => { activeTarget.value = 'gpu'; step.value = 2 }, 4000)
  setTimeout(() => { activeTarget.value = 'cloud'; step.value = 3 }, 7000)
})
</script>

<style scoped>
.hscale {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  width: 100%;
}

/* ===== TITLE ===== */
.hscale-title-row {
  text-align: center;
  animation: hfadeIn 0.6s ease-out both;
}
.hscale-title {
  font-size: 2.8rem;
  font-weight: 900;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #b1c7f3;
  letter-spacing: 0.08em;
  line-height: 1.1;
}
.hscale-subtitle {
  font-size: 2.5rem;
  font-weight: 800;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #fea619;
  letter-spacing: 0.15em;
  margin-top: 0.1rem;
}

/* ===== SWITCH AREA ===== */
.hscale-switch-area {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.4rem;
  opacity: 0;
  animation: hfadeIn 0.5s ease-out 0.6s both;
}
.hscale-switch-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.5rem;
  font-weight: 700;
  color: #778cb5;
  letter-spacing: 0.15em;
}

/* ---- Options ---- */
.hscale-options {
  display: flex;
  gap: 1.2rem;
}
.hscale-option {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.1rem;
  padding: 0.4rem 0.8rem;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 8px;
  cursor: pointer;
  transition: border-color 0.4s, background 0.4s, box-shadow 0.4s, transform 0.3s;
}
.hscale-option:hover {
  transform: translateY(-2px);
}
.hscale-option-active {
  border-color: #009d8d;
  background: #00120f;
}
.hscale-option-icon {
  color: #778cb5;
  transition: color 0.4s;
}
.hscale-option-active .hscale-option-icon {
  color: #009d8d;
}
.hscale-option-name {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  font-weight: 800;
  color: #ccc;
  transition: color 0.4s;
}
.hscale-option-active .hscale-option-name {
  color: #009d8d;
}
.hscale-option-desc {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.45rem;
  font-weight: 600;
  color: #778cb5;
}

/* ---- Switch thumb ---- */
.hscale-switch-bar {
  width: 100%;
  display: flex;
  justify-content: center;
}
.hscale-switch-track {
  width: 200px;
  height: 6px;
  background: #32476c;
  border-radius: 3px;
  position: relative;
}
.hscale-switch-thumb {
  width: 50px;
  height: 12px;
  background: #009d8d;
  border-radius: 6px;
  position: absolute;
  top: -3px;
  transition: left 0.5s cubic-bezier(0.34,1.56,0.64,1);
}
.hscale-thumb-cpu   { left: 0; }
.hscale-thumb-gpu   { left: 75px; }
.hscale-thumb-cloud { left: 150px; }

/* ===== VIS PANELS ===== */
.hscale-vis {
  width: 100%;
  display: flex;
  justify-content: center;
}
.hscale-vis-panel {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  padding: 0.4rem 0.8rem;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 8px;
  opacity: 0;
  animation: hfadeIn 0.4s ease-out both;
}
.hscale-vis-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.5rem;
  font-weight: 700;
  color: #778cb5;
  letter-spacing: 0.1em;
}

/* ---- CPU grid ---- */
.hscale-cpu-grid {
  display: grid;
  grid-template-columns: repeat(4, 20px);
  gap: 3px;
}
.hscale-cpu-core {
  width: 20px;
  height: 20px;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 3px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.hscale-core-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #778cb5;
}

/* ---- GPU grid ---- */
.hscale-gpu-grid {
  display: grid;
  grid-template-columns: repeat(8, 16px);
  gap: 2px;
}
.hscale-gpu-core {
  width: 16px;
  height: 14px;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 2px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.hscale-gpu-core .hscale-core-dot {
  width: 4px;
  height: 4px;
}

/* ---- Cloud cluster ---- */
.hscale-cloud-cluster {
  display: flex;
  gap: 0.5rem;
  align-items: center;
}
.hscale-cloud-node {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.15rem;
}
.hscale-node-box {
  width: 32px;
  padding: 0.2rem;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  gap: 2px;
}
.hscale-node-row {
  height: 4px;
  background: #1a2a3a;
  border-radius: 1px;
}
.hscale-node-conn {
  width: 2px;
  height: 8px;
  background: #32476c;
}

/* ---- Flow row ---- */
.hscale-flow-row {
  display: flex;
  gap: 0.3rem;
  align-items: center;
}
.hscale-flow-dot {
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: #009d8d;
  opacity: 0;
  animation: hdotPulse 1.0s ease-in-out infinite;
}
.hscale-flow-dot:nth-child(1) { animation-delay: 0.0s; }
.hscale-flow-dot:nth-child(2) { animation-delay: 0.15s; }
.hscale-flow-dot:nth-child(3) { animation-delay: 0.3s; }
.hscale-flow-dot:nth-child(4) { animation-delay: 0.45s; }
.hscale-flow-dot:nth-child(5) { animation-delay: 0.6s; }
.hscale-flow-dot:nth-child(6) { animation-delay: 0.75s; }
.hscale-flow-dot:nth-child(7) { animation-delay: 0.9s; }
.hscale-flow-dot:nth-child(8) { animation-delay: 1.05s; }
.hscale-flow-dot:nth-child(9) { animation-delay: 1.2s; }
.hscale-flow-dot:nth-child(10) { animation-delay: 1.35s; }
.hscale-flow-dot:nth-child(11) { animation-delay: 1.5s; }
.hscale-flow-dot:nth-child(12) { animation-delay: 1.65s; }
.hscale-flow-wide {
  gap: 0.15rem;
}
.hscale-flow-cloud {
  gap: 0.2rem;
}

/* ===== MOTTO ===== */
.hscale-motto {
  display: flex;
  gap: 0.35rem;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 1rem;
  font-weight: 700;
  opacity: 0;
  animation: hfadeIn 0.6s ease-out 2.2s both;
}
.hscale-motto-line {
  color: #778cb5;
}
.hscale-motto-em {
  color: #009d8d;
}

/* ===== TRANSITIONS ===== */
.hscale-fade-enter-active {
  animation: hfadeIn 0.4s ease-out;
}
.hscale-fade-leave-active {
  animation: hfadeIn 0.25s ease-in reverse;
}

/* ===== KEYFRAMES ===== */
@keyframes hfadeIn {
  from { opacity: 0; transform: translateY(8px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes hdotPulse {
  0%,100% { opacity: 0.3; transform: scale(0.8); }
  50%     { opacity: 1; transform: scale(1.2); }
}

.slidev-code {
  font-size: 1.3rem !important;
}
</style>
