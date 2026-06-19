<template>
  <div class="chain">
    <!-- ===== TITLE ===== -->
    <div class="chain-title-row">
      <div class="chain-title">Compiler Optimization:</div>
      <div class="chain-subtitle">Operator Chaining</div>
    </div>

    <!-- ===== CODE REMINDER ===== -->
    <pre class="slidev-code"><code class="language-java">weights^^ += learningRate * gradients^</code></pre>

    <!-- ===== TWO PATHS ===== -->
    <div class="chain-paths">
      <!-- ---- NAIVE PATH (top) ---- -->
      <div class="chain-naive" :class="{ 'chain-naive-done': phase >= 2 }">
        <div class="chain-path-label chain-naive-label">Naiver Weg</div>
        <div class="chain-naive-flow">
          <div class="chain-step">
            <span class="chain-op">learningRate</span>
            <span class="chain-op-sym">×</span>
            <span class="chain-op">gradients</span>
            <span class="chain-arr">→</span>
          </div>
          <!-- temp matrix box -->
          <Transition name="chain-pop">
            <div v-if="phase >= 1" class="chain-temp-box">
              <div class="chain-temp-label">[Temp Matrix]</div>
              <Transition name="chain-fade">
                <div v-if="phase >= 2" class="chain-temp-x">
                  <div class="chain-x-line chain-x-a"></div>
                  <div class="chain-x-line chain-x-b"></div>
                </div>
              </Transition>
            </div>
          </Transition>
          <div class="chain-step" :class="{ 'chain-fade-out': phase >= 2 }">
            <span class="chain-arr">→</span>
            <span class="chain-op">weights</span>
            <span class="chain-op-sym">+=</span>
          </div>
        </div>
      </div>

      <!-- ---- CONCURNAS PATH (bottom) ---- -->
      <div class="chain-concurnas" :class="{ 'chain-concurnas-emerge': phase >= 2 }">
        <div class="chain-path-label chain-concurnas-label">Concurnas-Weg</div>
        <div class="chain-concurnas-flow">
          <!-- gear icon -->
          <div class="chain-gear">
            <div class="chain-gear-icon">⚙</div>
            <div class="chain-gear-text">Compiler</div>
          </div>
          <!-- arrows in -->
          <div class="chain-arrows-in">
            <div class="chain-in-arrow">
              <span class="chain-in-label">learningRate</span>
              <span class="chain-in-sym">→</span>
            </div>
            <div class="chain-in-arrow">
              <span class="chain-in-label">gradients</span>
              <span class="chain-in-sym">→</span>
            </div>
          </div>
          <!-- fused step -->
          <Transition name="chain-pop">
            <div v-if="phase >= 2" class="chain-fused">
              <div class="chain-fused-icon">⚡</div>
              <div class="chain-fused-label">[Fused Step]</div>
            </div>
          </Transition>
          <!-- combined beam out -->
          <div v-if="phase >= 2" class="chain-beam">
            <div class="chain-beam-arr">➡</div>
            <div class="chain-beam-label">weights</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const phase = ref(0)

onMounted(() => {
  // phase 0→1 after 0.8s: temp matrix appears
  setTimeout(() => { phase.value = 1 }, 800)
  // phase 1→2 after 2.5s: X + dissolve + fused step emerges
  setTimeout(() => { phase.value = 2 }, 3300)
})
</script>

<style scoped>
.chain {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.6rem;
  width: 100%;
}

/* ===== TITLE ===== */
.chain-title-row {
  text-align: center;
  animation: cfadeIn 0.6s ease-out both;
}
.chain-title {
  font-size: 2.8rem;
  font-weight: 900;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #b1c7f3;
  text-shadow: 0 0 40px rgba(177,199,243,0.5), 0 0 80px rgba(177,199,243,0.2);
  letter-spacing: 0.08em;
  line-height: 1.1;
}
.chain-subtitle {
  font-size: 2rem;
  font-weight: 800;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #fea619;
  text-shadow: 0 0 30px rgba(254,166,25,0.4);
  letter-spacing: 0.12em;
  margin-top: 0.1rem;
}

/* ===== PATHS CONTAINER ===== */
.chain-paths {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.2rem;
  width: 100%;
}

/* ===== NAIVE PATH ===== */
.chain-naive {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  padding: 0.5rem 1.5rem;
  background: linear-gradient(145deg,#000f27,#0b2447);
  border: 2px solid #32476c;
  border-radius: 10px;
  opacity: 0;
  animation: cfadeIn 0.6s ease-out 0.6s both;
  transition: opacity 0.8s, border-color 0.8s;
}
.chain-naive-done {
  opacity: 0.25;
  border-color: #3a1a1a;
}
.chain-naive-label {
  color: #ff5555;
}
.chain-naive-flow {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  flex-wrap: wrap;
  justify-content: center;
}
.chain-step {
  display: flex;
  align-items: center;
  gap: 0.3rem;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.85rem;
  font-weight: 600;
  color: #ccc;
}
.chain-fade-out {
  opacity: 0.3;
  transition: opacity 0.6s;
}
.chain-op-sym {
  color: #b1c7f3;
  font-weight: 800;
  margin: 0 0.15rem;
}
.chain-arr {
  color: #778cb5;
  font-size: 1rem;
}

/* ===== TEMP MATRIX ===== */
.chain-temp-box {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0.35rem 0.7rem;
  background: #2a0a0a;
  border: 2px solid #ff3333;
  border-radius: 6px;
  box-shadow: 0 0 20px rgba(255,51,51,0.3);
}
.chain-temp-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  font-weight: 800;
  color: #ff5555;
  letter-spacing: 0.05em;
}

/* X mark */
.chain-temp-x {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
.chain-x-line {
  position: absolute;
  width: 120%;
  height: 3px;
  background: #ff3333;
  border-radius: 2px;
  box-shadow: 0 0 12px rgba(255,51,51,0.6);
}
.chain-x-a { transform: rotate(45deg); }
.chain-x-b { transform: rotate(-45deg); }

/* ===== CONCURNAS PATH ===== */
.chain-concurnas {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  padding: 0.5rem 1.5rem;
  background: linear-gradient(145deg,#002a25,#0b2447);
  border: 2px solid #32476c;
  border-radius: 10px;
  opacity: 0;
  animation: cfadeIn 0.6s ease-out 0.9s both;
  transition: border-color 0.8s, box-shadow 0.8s;
}
.chain-concurnas-emerge {
  border-color: #009d8d;
  box-shadow: 0 0 30px rgba(0,157,141,0.15), 0 0 60px rgba(0,157,141,0.05);
}
.chain-concurnas-label {
  color: #009d8d;
}
.chain-concurnas-flow {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  flex-wrap: wrap;
  justify-content: center;
}

/* Gear icon */
.chain-gear {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.1rem;
}
.chain-gear-icon {
  font-size: 1.6rem;
  animation: cspin 3s linear infinite;
}
.chain-gear-text {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.5rem;
  font-weight: 700;
  color: #778cb5;
}

/* Arrows into gear */
.chain-arrows-in {
  display: flex;
  flex-direction: column;
  gap: 0.15rem;
}
.chain-in-arrow {
  display: flex;
  align-items: center;
  gap: 0.25rem;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  font-weight: 600;
  animation: cfadeIn 0.5s ease-out 1.2s both;
}
.chain-in-arrow:nth-child(2) {
  animation-delay: 1.4s;
}
.chain-in-label {
  color: #fea619;
}
.chain-in-sym {
  color: #009d8d;
}

/* Fused step */
.chain-fused {
  display: flex;
  align-items: center;
  gap: 0.3rem;
  padding: 0.3rem 0.6rem;
  background: #00120f;
  border: 2px solid #009d8d;
  border-radius: 8px;
  box-shadow: 0 0 25px rgba(0,157,141,0.3), 0 0 50px rgba(0,157,141,0.1);
}
.chain-fused-icon {
  font-size: 1.2rem;
  animation: cflash 0.8s ease-in-out infinite alternate;
}
.chain-fused-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  font-weight: 800;
  color: #009d8d;
  letter-spacing: 0.05em;
}

/* Combined beam */
.chain-beam {
  display: flex;
  align-items: center;
  gap: 0.3rem;
  opacity: 0;
  animation: cbeamIn 0.6s ease-out 4.0s both;
}
.chain-beam-arr {
  font-size: 1.8rem;
  color: #009d8d;
  text-shadow: 0 0 20px rgba(0,157,141,0.6);
  animation: cbeamPulse 0.8s ease-in-out infinite alternate;
}
.chain-beam-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.85rem;
  font-weight: 800;
  color: #fea619;
}

/* ===== PATH LABELS ===== */
.chain-path-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.6rem;
  font-weight: 700;
  letter-spacing: 0.1em;
}

/* ===== TRANSITIONS ===== */
.chain-pop-enter-active {
  animation: cpopIn 0.4s ease-out;
}
.chain-pop-leave-active {
  animation: cpopIn 0.3s ease-in reverse;
}
.chain-fade-enter-active {
  transition: opacity 0.3s;
}
.chain-fade-leave-active {
  transition: opacity 0.4s;
}
.chain-fade-enter-from,
.chain-fade-leave-to {
  opacity: 0;
}

/* ===== KEYFRAMES ===== */
@keyframes cfadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes cpopIn {
  from { opacity: 0; transform: scale(0.6); }
  to   { opacity: 1; transform: scale(1); }
}
@keyframes cspin {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}
@keyframes cflash {
  from { opacity: 0.7; transform: scale(1); }
  to   { opacity: 1; transform: scale(1.15); }
}
@keyframes cbeamIn {
  from { opacity: 0; transform: translateX(-20px); }
  to   { opacity: 1; transform: translateX(0); }
}
@keyframes cbeamPulse {
  from { opacity: 0.7; }
  to   { opacity: 1; }
}

.slidev-code {
  font-size: 1.3rem !important;
}
</style>
