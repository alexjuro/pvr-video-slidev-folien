<template>
  <div class="chain">
    <!-- ===== TITLE ===== -->
    <div class="chain-title-row">
      <div class="chain-title">Operator Chaining</div>
    </div>

    <!-- ===== CODE REMINDER ===== -->
    <pre
      class="slidev-code"
    ><code class="language-java">weights^^ += learningRate * gradients^</code></pre>

    <!-- ===== TWO PATHS ===== -->
    <div class="chain-paths">
      <!-- ---- NAIVE PATH (top) ---- -->
      <div class="chain-naive">
        <div class="chain-path-label chain-naive-label">Naiver Weg</div>
        <div class="chain-naive-flow">
          <div class="chain-step">
            <span class="chain-op">learningRate</span>
            <span class="chain-op-sym">×</span>
            <span class="chain-op">gradients</span>
            <span class="chain-arr">→</span>
          </div>

          <!-- Temp matrix + X (box click 1, X click 2) -->
          <div v-click="1" class="chain-temp-box">
            <div class="chain-temp-label">[Temp Matrix]</div>
            <div v-click="2" class="chain-temp-x">
              <div class="chain-x-line chain-x-a"></div>
              <div class="chain-x-line chain-x-b"></div>
            </div>
          </div>

          <div class="chain-step chain-step-last">
            <span class="chain-arr">→</span>
            <span class="chain-op">weights</span>
            <span class="chain-op-sym">+=</span>
          </div>
        </div>
      </div>

      <!-- ---- CONCURNAS PATH (bottom) ---- -->
      <div class="chain-concurnas">
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
          <!-- fused step (click 2) -->
          <div v-click="2" class="chain-fused">
            <div class="chain-fused-icon">⚡</div>
            <div class="chain-fused-label">[Fused Step]</div>
          </div>
          <!-- combined beam (click 2) -->
          <div v-click="2" class="chain-beam">
            <div class="chain-beam-arr">➡</div>
            <div class="chain-beam-label">weights</div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- REFERENCE -->
  <span class="ref">[4]</span>
</template>

<script setup></script>

<style scoped>
.chain {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 1.5rem;
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
  font-family: "JetBrains Mono", "Fira Code", monospace;
  color: #b1c7f3;
  letter-spacing: 0.08em;
  line-height: 1.1;
}
.chain-subtitle {
  font-size: 2rem;
  font-weight: 800;
  font-family: "JetBrains Mono", "Fira Code", monospace;
  color: #fea619;
  letter-spacing: 0.12em;
  margin-top: 0.1rem;
}

/* ===== PATHS CONTAINER ===== */
.chain-paths {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
  width: 100%;
}

/* ===== NAIVE PATH ===== */
.chain-naive {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  padding: 0.5rem 1.5rem;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 10px;
  opacity: 0;
  animation: cfadeIn 0.6s ease-out 0.6s both;
  transition:
    opacity 0.8s,
    border-color 0.8s;
}
.chain-paths:has(.chain-temp-x:not(.slidev-vclick-hidden)) .chain-naive {
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
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.85rem;
  font-weight: 600;
  color: #ccc;
}
.chain-paths:has(.chain-temp-x:not(.slidev-vclick-hidden)) .chain-step-last {
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
  animation: cpopIn 0.4s ease-out both;
}
.chain-temp-label {
  font-family: "JetBrains Mono", "Fira Code", monospace;
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
  animation: cpopIn 0.3s ease-out both;
}
.chain-x-line {
  position: absolute;
  width: 120%;
  height: 3px;
  background: #ff3333;
  border-radius: 2px;
}
.chain-x-a {
  transform: rotate(45deg);
}
.chain-x-b {
  transform: rotate(-45deg);
}

/* ===== CONCURNAS PATH ===== */
.chain-concurnas {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  padding: 0.5rem 1.5rem;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 10px;
  opacity: 0;
  animation: cfadeIn 0.6s ease-out 0.9s both;
  transition: border-color 0.8s;
}
.chain-paths:has(.chain-fused:not(.slidev-vclick-hidden)) .chain-concurnas {
  border-color: #009d8d;
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
  font-family: "JetBrains Mono", "Fira Code", monospace;
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
  font-family: "JetBrains Mono", "Fira Code", monospace;
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
  animation: cpopIn 0.4s ease-out both;
}
.chain-fused-icon {
  font-size: 1.2rem;
  animation: cflash 0.8s ease-in-out infinite alternate;
}
.chain-fused-label {
  font-family: "JetBrains Mono", "Fira Code", monospace;
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
  animation: cfadeIn 0.5s ease-out 0.2s both;
}
.chain-beam-arr {
  font-size: 1.8rem;
  color: #009d8d;
}
.chain-beam-label {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.85rem;
  font-weight: 800;
  color: #fea619;
}

/* ===== PATH LABELS ===== */
.chain-path-label {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.6rem;
  font-weight: 700;
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

@keyframes cfadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
@keyframes cpopIn {
  from {
    opacity: 0;
    transform: scale(0.6);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}
@keyframes cspin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
@keyframes cflash {
  from {
    opacity: 0.7;
    transform: scale(1);
  }
  to {
    opacity: 1;
    transform: scale(1.15);
  }
}

.slidev-code {
  font-size: 1.3rem !important;
}
</style>
