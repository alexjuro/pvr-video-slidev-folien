<template>
  <div class="summary">
    <!-- ===== HERO ARROW ===== -->
    <div class="summary-hero">
      <div class="summary-code-label">Code</div>
      <div class="summary-big-arrow">
        <div class="summary-arrow-body"></div>
        <div class="summary-arrow-head">➡</div>
      </div>
      <div class="summary-perf-label">Leistung</div>
    </div>

    <!-- ===== STEP 1: WORLDS + MOTTO + CHECKS ===== -->
    <div v-click="1" class="summary-worlds-wrap">
      <!-- Step 2 trigger -->
      <div v-click="2" class="sum-step2"></div>

      <!-- OLD WORLD -->
      <div class="summary-old">
        <div class="summary-world-label">Traditionell</div>
        <div class="summary-bullets">
          <div class="sum-bullet">
            <span class="sum-bullet-icon">✗</span> synchronisiert
          </div>
          <div class="sum-bullet">
            <span class="sum-bullet-icon">✗</span> Thread
          </div>
          <div class="sum-bullet">
            <span class="sum-bullet-icon">✗</span> Lock
          </div>
        </div>
      </div>

      <!-- CONC WORLD -->
      <div class="summary-conc">
        <div class="summary-world-label summary-conc-label">Concurnas</div>
        <div class="summary-vec">
          <div class="summary-vec-label">Parallele Vektorisierung</div>
          <div class="summary-vec-lanes">
            <div v-for="i in 4" :key="i" class="summary-vec-lane">
              <div class="summary-vec-cell summary-vec-in">x</div>
              <div class="summary-vec-op">▶</div>
              <div class="summary-vec-cell summary-vec-out">y</div>
            </div>
          </div>
          <div class="summary-vec-hint">elementweise parallel</div>
        </div>
      </div>

      <!-- ===== MOTTO ===== -->
      <div class="summary-motto">
        <span class="summary-motto-code">Write once.</span>
        <span class="summary-motto-em"> Execute everywhere.</span>
      </div>

      <!-- ===== CHECKS ===== -->
      <div class="summary-checks">
        <div class="sum-check">
          <span class="sum-check-icon">✓</span> Kein manuelles Thread-Management
        </div>
        <div class="sum-check">
          <span class="sum-check-icon">✓</span> Kein Boilerplate-Code
        </div>
        <div class="sum-check">
          <span class="sum-check-icon">✓</span> Hardware-agnostisch
        </div>
      </div>
    </div>

    <!-- ===== STEP 3: FINAL BRAND ===== -->
    <div v-click="3" class="summary-final">
      <div class="summary-final-rule"></div>
      <div class="summary-final-name">Concurnas</div>
    </div>
  </div>

  <!-- REFERENCE -->
  <span class="ref">[4]</span>
</template>

<script setup>
// No JS animation logic needed — all steps are v-click driven
</script>

<style scoped>
.summary {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.4rem;
  width: 100%;
}

/* ===== STEP TRIGGER ===== */
.sum-step2 {
  position: absolute;
  pointer-events: none;
  opacity: 0;
  width: 0;
  height: 0;
}

/* ===== HERO ARROW ===== */
.summary-hero {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  opacity: 0;
  animation: sfadeIn 0.6s ease-out 0.3s both;
}
.summary-code-label,
.summary-perf-label {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.9rem;
  font-weight: 700;
  color: #778cb5;
}
.summary-perf-label {
  color: #fea619;
}
.summary-big-arrow {
  display: flex;
  align-items: center;
  gap: 0.1rem;
}
.summary-arrow-body {
  width: 60px;
  height: 2px;
  background: linear-gradient(90deg, #778cb5, #fea619);
  border-radius: 1px;
}
.summary-arrow-head {
  font-size: 1.2rem;
  color: #fea619;
}

/* ===== WORLDS WRAPPER (step 1 group) ===== */
.summary-worlds-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  position: relative;
}

/* ===== WORLDS ===== */
.summary-worlds {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  width: 100%;
}
.summary-world-label {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.5rem;
  font-weight: 700;
  color: #778cb5;
  letter-spacing: 0.1em;
}

/* ---- Old world ---- */
.summary-old {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.1rem;
  transition: opacity 0.8s;
}
.summary-worlds-wrap:has(.sum-step2:not(.slidev-vclick-hidden)) .summary-old {
  opacity: 0.15;
}

/* ---- Traditional bullets ---- */
.summary-bullets {
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
  padding: 0.3rem 0.6rem;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 8px;
  min-width: 160px;
}
.sum-bullet {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.6rem;
  font-weight: 600;
  color: #ff5555;
  display: flex;
  align-items: center;
  gap: 0.25rem;
}
.sum-bullet-icon {
  color: #ff5555;
  font-weight: 900;
  font-size: 0.65rem;
  opacity: 0.7;
}

/* ---- Conc world ---- */
.summary-conc {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.1rem;
  opacity: 0.3;
  transition: opacity 0.8s;
}
.summary-worlds-wrap:has(.sum-step2:not(.slidev-vclick-hidden)) .summary-conc {
  opacity: 1;
}
.summary-conc-label {
  color: #009d8d;
}

/* ===== Vectorization widget ===== */
.summary-vec {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  padding: 0.4rem 0.6rem;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 8px;
  transition: border-color 0.6s;
}
.summary-worlds-wrap:has(.sum-step2:not(.slidev-vclick-hidden)) .summary-vec {
  border-color: #009d8d;
}
.summary-vec-label {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.5rem;
  font-weight: 700;
  color: #009d8d;
  letter-spacing: 0.1em;
}
.summary-vec-lanes {
  display: flex;
  flex-direction: column;
  gap: 0.2rem;
}
.summary-vec-lane {
  display: flex;
  align-items: center;
  gap: 0.3rem;
}
.summary-vec-cell {
  width: 24px;
  height: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.5rem;
  font-weight: 700;
}
.summary-vec-in {
  border: 1.5px solid #32476c;
  border-radius: 3px;
  color: #ccc;
  background: #000f27;
}
.summary-vec-out {
  border: 1.5px solid #009d8d;
  border-radius: 3px;
  color: #009d8d;
  background: #00120f;
}
.summary-vec-op {
  font-size: 0.55rem;
  color: #fea619;
  line-height: 1;
}
.summary-vec-hint {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.4rem;
  font-weight: 600;
  color: #778cb5;
  letter-spacing: 0.08em;
  margin-top: 0.1rem;
}

/* ===== CHECKS ===== */
.summary-checks {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  justify-content: center;
}
.sum-check {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.55rem;
  font-weight: 600;
  color: #ccc;
  display: flex;
  align-items: center;
  gap: 0.2rem;
  opacity: 0;
}
.summary-worlds-wrap:has(.sum-step2:not(.slidev-vclick-hidden)) .sum-check {
  animation: sfadeIn 0.5s ease-out forwards;
}
.summary-worlds-wrap:has(.sum-step2:not(.slidev-vclick-hidden))
  .sum-check:nth-child(1) {
  animation-delay: 0s;
}
.summary-worlds-wrap:has(.sum-step2:not(.slidev-vclick-hidden))
  .sum-check:nth-child(2) {
  animation-delay: 0.2s;
}
.summary-worlds-wrap:has(.sum-step2:not(.slidev-vclick-hidden))
  .sum-check:nth-child(3) {
  animation-delay: 0.4s;
}
.sum-check-icon {
  color: #009d8d;
  font-weight: 900;
  font-size: 0.7rem;
}

/* ===== MOTTO ===== */
.summary-motto {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.95rem;
  font-weight: 700;
  opacity: 0;
  transition: opacity 0.6s;
}
.summary-worlds-wrap:has(.sum-step2:not(.slidev-vclick-hidden)) .summary-motto {
  opacity: 1;
}
.summary-motto-code {
  color: #778cb5;
}
.summary-motto-em {
  color: #009d8d;
}

/* ===== FINAL BRAND (step 3) ===== */
.summary-final {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.15rem;
}
.summary-final-rule {
  width: 180px;
  height: 1px;
  background: linear-gradient(90deg, transparent, #009d8d, transparent);
  margin-bottom: 0.15rem;
}
.summary-final-name {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 2.2rem;
  font-weight: 900;
  color: #009d8d;
  letter-spacing: 0.2em;
  animation: sglowPulse 2s ease-in-out infinite;
}
.summary-final-tag {
  font-family: "JetBrains Mono", "Fira Code", monospace;
  font-size: 0.55rem;
  font-weight: 600;
  color: #778cb5;
  letter-spacing: 0.15em;
}

/* ===== KEYFRAMES ===== */
.ref {
  position: fixed;
  bottom: 1rem;
  right: 1.5rem;
  font-size: 0.8rem;
  color: #999;
}

@keyframes sfadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
@keyframes sglowPulse {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.7;
  }
}
</style>
