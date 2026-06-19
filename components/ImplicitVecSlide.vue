<template>
  <div class="iv">
    <!-- ===== TITLE ===== -->
    <div class="iv-title-row">
      <div class="iv-title">Clean Syntax:</div>
      <div class="iv-subtitle">Implicit Vectorization</div>
    </div>

    <!-- sine wave background -->
    <svg class="iv-sine-bg" viewBox="0 0 600 120" preserveAspectRatio="none">
      <path d="M0,60 Q75,0 150,60 T300,60 T450,60 T600,60" fill="none" stroke="#0f3460" stroke-width="1.5" opacity="0.15" />
      <path d="M0,60 Q75,0 150,60 T300,60 T450,60 T600,60" fill="none" stroke="#0f3460" stroke-width="0.8" opacity="0.08"
        transform="translate(0,15)" />
      <path d="M0,60 Q75,0 150,60 T300,60 T450,60 T600,60" fill="none" stroke="#0f3460" stroke-width="0.8" opacity="0.08"
        transform="translate(0,-15)" />
    </svg>

    <!-- ===== CODE COMPARISON ===== -->
    <div class="iv-code-area">
      <!-- scalar (grayed out) -->
      <div class="iv-scalar">
        <pre class="iv-code-line"><code><span class="iv-gray">y = sin(x)</span></code></pre>
      </div>

      <!-- concurnas -->
      <div class="iv-concurnas">
        <pre class="iv-code-line"><code><span class="iv-lhs">y</span><span class="iv-op"> = sin(</span><span class="iv-var">weights</span><span class="iv-op">)</span></code></pre>
      </div>

      <!-- compiler transpile line -->
      <Transition name="iv-fade">
        <div v-if="phase >= 4" class="iv-transpile">
          <pre class="iv-code-line iv-code-small"><code><span class="iv-comment">// Compiler transpiles to:</span>
<span class="iv-lhs">y</span><span class="iv-op"> = sin(</span><span class="iv-var">weights</span><span class="iv-hat-inline">^</span><span class="iv-op">)</span></code></pre>
        </div>
      </Transition>
    </div>

    <!-- ===== ARRAY GRID ===== -->
    <div v-if="phase >= 2" class="iv-array-wrap">
      <div class="iv-array" :class="{ 'iv-array-flooded': phase >= 5 }">
        <div
          v-for="(cell, i) in cells"
          :key="i"
          class="iv-cell"
          :class="{ 'iv-cell-changed': phase >= 5 }"
          :style="{ transitionDelay: `${4.8 + i * 0.06}s` }"
        >
          <span class="iv-cell-val">{{ phase >= 5 ? cell.after : cell.before }}</span>
        </div>
      </div>
      <!-- pulse line -->
      <div v-if="phase >= 5" class="iv-pulse-line"></div>
    </div>

    <!-- ===== COMPILER ICON ===== -->
    <Transition name="iv-pop">
      <div v-if="phase >= 3" class="iv-compiler-icon">
        <span class="iv-gear">⚙</span>
      </div>
    </Transition>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const phase = ref(0)

const raw = [0.10, 0.35, 0.60, 0.85, 0.95, 0.80, 0.50, 0.20, 0.02, 0.15, 0.45, 0.70, 0.90, 0.88, 0.65, 0.30]
const cells = raw.map((v, i) => ({
  before: v.toFixed(2),
  after: Math.sin(v * Math.PI).toFixed(2),
}))

onMounted(() => {
  // phase 0→1 after 0.5s: code appears
  setTimeout(() => { phase.value = 1 }, 500)
  // phase 1→2 after 1.5s: array slides in
  setTimeout(() => { phase.value = 2 }, 2000)
  // phase 2→3 after 1.0s: compiler icon
  setTimeout(() => { phase.value = 3 }, 3000)
  // phase 3→4 after 0.8s: transpile line with ^
  setTimeout(() => { phase.value = 4 }, 3800)
  // phase 4→5 after 1.0s: flood the array
  setTimeout(() => { phase.value = 5 }, 4800)
})
</script>

<style scoped>
.iv {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.6rem;
  width: 100%;
  position: relative;
  overflow: hidden;
}

/* ===== SINE BG ===== */
.iv-sine-bg {
  position: absolute;
  bottom: 20px;
  width: 100%;
  height: 120px;
  pointer-events: none;
  z-index: 0;
}

/* ===== TITLE ===== */
.iv-title-row {
  text-align: center;
  animation: ivfadeIn 0.6s ease-out both;
  z-index: 1;
}
.iv-title {
  font-size: 2.8rem;
  font-weight: 900;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #00e5ff;
  text-shadow: 0 0 40px rgba(0,229,255,0.5), 0 0 80px rgba(0,229,255,0.2);
  letter-spacing: 0.08em;
  line-height: 1.1;
}
.iv-subtitle {
  font-size: 2rem;
  font-weight: 800;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #ffa500;
  text-shadow: 0 0 30px rgba(255,165,0,0.4);
  letter-spacing: 0.12em;
  margin-top: 0.1rem;
}

/* ===== CODE ===== */
.iv-code-area {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.15rem;
  z-index: 1;
}
.iv-scalar {
  opacity: 0;
  animation: ivfadeIn 0.5s ease-out 0.3s both;
}
.iv-concurnas {
  padding: 0.25rem 1rem;
  background: #1a1a2e;
  border: 2px solid #0f3460;
  border-radius: 8px;
  opacity: 0;
  animation: ivfadeIn 0.6s ease-out 0.5s both;
}
.iv-code-line {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 1.1rem;
  font-weight: 600;
  margin: 0;
}
.iv-code-small {
  font-size: 0.8rem;
}
.iv-gray { color: #3a5a5a; }
.iv-lhs { color: #ffd700; }
.iv-op  { color: #7ec8e3; }
.iv-var { color: #ffd700; }
.iv-comment { color: #3a5a5a; font-style: italic; }
.iv-hat-inline {
  font-size: 1.1rem;
  font-weight: 900;
  color: #39ff14;
  text-shadow: 0 0 15px rgba(57,255,20,0.8), 0 0 30px rgba(57,255,20,0.4);
}

/* transpile line */
.iv-transpile {
  padding: 0.2rem 0.8rem;
  background: #0a1a0a;
  border: 1px solid #39ff14;
  border-radius: 6px;
  box-shadow: 0 0 15px rgba(57,255,20,0.1);
}

/* ===== ARRAY ===== */
.iv-array-wrap {
  position: relative;
  z-index: 1;
}
.iv-array {
  display: grid;
  grid-template-columns: repeat(8, 34px);
  gap: 2px;
  padding: 0.3rem;
  background: #1a1a2e;
  border: 2px solid #0f3460;
  border-radius: 8px;
  opacity: 0;
  animation: ivfadeIn 0.5s ease-out both;
}
.iv-array-flooded {
  border-color: #39ff14;
  box-shadow: 0 0 25px rgba(57,255,20,0.12);
  transition: border-color 0.6s, box-shadow 0.6s;
}
.iv-cell {
  height: 26px;
  background: #0a0a1a;
  border: 1px solid #0f3460;
  border-radius: 3px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.4s, border-color 0.4s, box-shadow 0.4s;
}
.iv-cell-changed {
  background: #0a1a0a;
  border-color: #39ff14;
  box-shadow: 0 0 8px rgba(57,255,20,0.15);
}
.iv-cell-val {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.5rem;
  font-weight: 700;
  color: #5a7a9a;
  transition: color 0.4s;
}
.iv-cell-changed .iv-cell-val {
  color: #39ff14;
}

/* pulse line */
.iv-pulse-line {
  position: absolute;
  top: 0;
  left: 0;
  width: 3px;
  height: 100%;
  background: linear-gradient(180deg, #39ff14, transparent);
  box-shadow: 0 0 15px rgba(57,255,20,0.5);
  animation: ivpulseSweep 0.8s ease-out 4.8s both;
}

/* ===== COMPILER ICON ===== */
.iv-compiler-icon {
  position: absolute;
  top: 30%;
  right: 12%;
  z-index: 2;
}
.iv-gear {
  font-size: 2rem;
  animation: ivspin 2s linear infinite;
  filter: drop-shadow(0 0 10px rgba(0,229,255,0.4));
}

/* ===== TRANSITIONS ===== */
.iv-fade-enter-active {
  transition: opacity 0.5s, transform 0.5s;
}
.iv-fade-leave-active {
  transition: opacity 0.3s;
}
.iv-fade-enter-from {
  opacity: 0;
  transform: translateY(-8px);
}
.iv-fade-leave-to {
  opacity: 0;
}
.iv-pop-enter-active {
  animation: ivpopIn 0.4s ease-out;
}
.iv-pop-leave-active {
  animation: ivpopIn 0.3s ease-in reverse;
}

/* ===== KEYFRAMES ===== */
@keyframes ivfadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes ivpopIn {
  from { opacity: 0; transform: scale(0.5); }
  to   { opacity: 1; transform: scale(1); }
}
@keyframes ivspin {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}
@keyframes ivpulseSweep {
  from { transform: translateX(0); }
  to   { transform: translateX(290px); }
}
</style>
