<template>
  <div class="summary">
    <!-- ===== TITLE ===== -->
    <div class="summary-title-row">
      <div class="summary-title">Performance</div>
      <div class="summary-subtitle">without Complexity</div>
    </div>

    <!-- ===== CENTRAL ARROW ===== -->
    <div class="summary-hero">
      <div class="summary-code-label">Code</div>
      <div class="summary-big-arrow">
        <div class="summary-arrow-body"></div>
        <div class="summary-arrow-head">➡</div>
      </div>
      <div class="summary-perf-label">Performance</div>
    </div>

    <!-- ===== TWO WORLDS ===== -->
    <div class="summary-worlds">
      <!-- OLD WORLD (spaghetti) -->
      <div class="summary-old" :class="{ 'summary-old-fade': phase >= 2 }">
        <div class="summary-world-label">Traditional</div>
        <svg class="summary-spaghetti" viewBox="0 0 300 70" width="300" height="70">
          <path d="M10,35 Q40,5 70,35 T130,35 T190,35 T250,35 T290,35"
                fill="none" stroke="#ff5555" stroke-width="1.5" opacity="0.55"
                class="sum-spag-line" />
          <path d="M10,20 Q50,50 90,20 T170,20 T210,50 T290,20"
                fill="none" stroke="#ff5555" stroke-width="1" opacity="0.35"
                class="sum-spag-line" />
          <path d="M10,50 Q30,20 70,50 T150,50 T190,20 T290,50"
                fill="none" stroke="#ff5555" stroke-width="1" opacity="0.35"
                class="sum-spag-line" />
          <!-- Labels -->
          <text x="200" y="12" fill="#ff5555" font-size="6" opacity="0.6"
                font-family="'JetBrains Mono','Fira Code',monospace">synchronized</text>
          <text x="20" y="65" fill="#ff5555" font-size="5" opacity="0.4"
                font-family="'JetBrains Mono','Fira Code',monospace">Thread</text>
          <text x="140" y="8" fill="#ff5555" font-size="5" opacity="0.4"
                font-family="'JetBrains Mono','Fira Code',monospace">Lock</text>
        </svg>
      </div>

      <!-- CONCURNAS WORLD (smooth stream) -->
      <div class="summary-conc" :class="{ 'summary-conc-emerge': phase >= 2 }">
        <div class="summary-world-label summary-conc-label">Concurnas</div>
        <div class="summary-stream-wrap">
          <!-- data stream line -->
          <div class="summary-stream-line" :class="{ 'summary-stream-active': phase >= 2 }">
            <div class="summary-stream-flow"></div>
          </div>

          <!-- three hardware icons along the stream -->
          <div class="summary-hw-row">
            <!-- CPU -->
            <div class="summary-hw-node" :class="{ 'summary-hw-lit': phase >= 2 }">
              <div class="summary-hw-icon">
                <svg viewBox="0 0 28 28" width="22" height="22">
                  <rect x="3" y="3" width="22" height="22" rx="3" fill="none" stroke="currentColor" stroke-width="1.5"/>
                  <rect x="8" y="8" width="12" height="12" rx="1" fill="none" stroke="currentColor" stroke-width="1"/>
                </svg>
              </div>
              <div class="summary-hw-name">CPU</div>
            </div>

            <!-- stream dot 1 -->
            <div v-if="phase >= 2" class="summary-stream-dot" style="animation-delay: 3.5s"></div>

            <!-- GPU -->
            <div class="summary-hw-node" :class="{ 'summary-hw-lit': phase >= 2 }">
              <div class="summary-hw-icon">
                <svg viewBox="0 0 36 24" width="28" height="20">
                  <rect x="1" y="1" width="34" height="22" rx="2" fill="none" stroke="currentColor" stroke-width="1.5"/>
                  <rect x="10" y="5" width="20" height="14" rx="1" fill="none" stroke="currentColor" stroke-width="0.8"/>
                  <rect x="3" y="7" width="4" height="10" rx="1" fill="none" stroke="currentColor" stroke-width="0.8"/>
                </svg>
              </div>
              <div class="summary-hw-name">GPU</div>
            </div>

            <!-- stream dot 2 -->
            <div v-if="phase >= 2" class="summary-stream-dot" style="animation-delay: 4.5s"></div>

            <!-- Cloud -->
            <div class="summary-hw-node" :class="{ 'summary-hw-lit': phase >= 2 }">
              <div class="summary-hw-icon">
                <svg viewBox="0 0 40 24" width="30" height="20">
                  <rect x="1" y="1" width="11" height="22" rx="1.5" fill="none" stroke="currentColor" stroke-width="1.2"/>
                  <rect x="2.5" y="3.5" width="8" height="2.5" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.6"/>
                  <rect x="2.5" y="9" width="8" height="2.5" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.6"/>
                  <rect x="2.5" y="14.5" width="8" height="2.5" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.6"/>
                  <rect x="14.5" y="1" width="11" height="22" rx="1.5" fill="none" stroke="currentColor" stroke-width="1.2"/>
                  <rect x="16" y="3.5" width="8" height="2.5" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.6"/>
                  <rect x="16" y="9" width="8" height="2.5" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.6"/>
                  <rect x="16" y="14.5" width="8" height="2.5" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.6"/>
                  <rect x="28" y="1" width="11" height="22" rx="1.5" fill="none" stroke="currentColor" stroke-width="1.2"/>
                  <rect x="29.5" y="3.5" width="8" height="2.5" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.6"/>
                  <rect x="29.5" y="9" width="8" height="2.5" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.6"/>
                  <rect x="29.5" y="14.5" width="8" height="2.5" rx="0.5" fill="none" stroke="currentColor" stroke-width="0.6"/>
                </svg>
              </div>
              <div class="summary-hw-name">Cloud</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- ===== MOTTO ===== -->
    <div class="summary-motto" :class="{ 'summary-motto-show': phase >= 2 }">
      <span class="summary-motto-code">Write once.</span>
      <span class="summary-motto-em"> Execute everywhere.</span>
    </div>

    <!-- ===== FINAL BRAND ===== -->
    <Transition name="sum-glow">
      <div v-if="phase >= 3" class="summary-final">
        <div class="summary-final-rule"></div>
        <div class="summary-final-name">Concurnas</div>
        <div class="summary-final-tag">Vectorized by default</div>
      </div>
    </Transition>

    <!-- ===== CHECKMARKS ===== -->
    <Transition name="sum-fade">
      <div v-if="phase >= 2" class="summary-checks">
        <div class="sum-check"><span class="sum-check-icon">✓</span> No manual thread management</div>
        <div class="sum-check"><span class="sum-check-icon">✓</span> Zero boilerplate</div>
        <div class="sum-check"><span class="sum-check-icon">✓</span> Hardware-agnostic</div>
      </div>
    </Transition>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const phase = ref(0)

onMounted(() => {
  // phase 0→1 after 0.8s: hero arrow + old world appear
  setTimeout(() => { phase.value = 1 }, 800)
  // phase 1→2 after 2.5s: old fades, concurnas emerges
  setTimeout(() => { phase.value = 2 }, 3300)
  // phase 2→3 after 3.0s: final brand glows
  setTimeout(() => { phase.value = 3 }, 6300)
})
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

/* ===== TITLE ===== */
.summary-title-row {
  text-align: center;
  animation: sfadeIn 0.6s ease-out both;
}
.summary-title {
  font-size: 3rem;
  font-weight: 900;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #009d8d;
  text-shadow: 0 0 40px rgba(0,157,141,0.5), 0 0 80px rgba(0,157,141,0.2);
  letter-spacing: 0.08em;
  line-height: 1.1;
}
.summary-subtitle {
  font-size: 1.8rem;
  font-weight: 700;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #fea619;
  text-shadow: 0 0 20px rgba(254,166,25,0.3);
  letter-spacing: 0.12em;
  margin-top: 0.05rem;
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
  font-family: 'JetBrains Mono','Fira Code',monospace;
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

/* ===== WORLDS ===== */
.summary-worlds {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  width: 100%;
}
.summary-world-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
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
.summary-old-fade {
  opacity: 0.15;
}
.summary-spaghetti {
  display: block;
}

/* ---- Concurnas world ---- */
.summary-conc {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.1rem;
  opacity: 0;
  transition: opacity 0.8s;
}
.summary-conc-emerge {
  opacity: 1;
}
.summary-conc-label {
  color: #009d8d;
}
.summary-stream-wrap {
  position: relative;
  padding: 0.3rem 0.5rem;
  background: #000f27;
  border: 2px solid #32476c;
  border-radius: 8px;
  transition: border-color 0.6s, box-shadow 0.6s;
}
.summary-conc-emerge .summary-stream-wrap {
  border-color: #009d8d;
  box-shadow: 0 0 25px rgba(0,157,141,0.1);
}

/* ---- Stream line ---- */
.summary-stream-line {
  position: absolute;
  top: 60%;
  left: 8%;
  width: 84%;
  height: 2px;
  background: #32476c;
  border-radius: 1px;
  z-index: 0;
}
.summary-stream-active {
  background: linear-gradient(90deg, #009d8d, #b1c7f3, #fea619);
  box-shadow: 0 0 12px rgba(0,157,141,0.3);
}
.summary-stream-flow {
  position: absolute;
  top: -3px;
  left: 0;
  width: 12px;
  height: 8px;
  border-radius: 50%;
  background: #009d8d;
  box-shadow: 0 0 15px rgba(0,157,141,0.6);
  animation: sstreamFlow 2.5s linear infinite;
}

/* stream dot pulse */
.summary-stream-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #009d8d;
  box-shadow: 0 0 10px rgba(0,157,141,0.5);
  animation: sdotPulse 1.5s ease-in-out infinite;
}

/* ---- HW row ---- */
.summary-hw-row {
  display: flex;
  align-items: center;
  gap: 1rem;
  position: relative;
  z-index: 1;
}
.summary-hw-node {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.1rem;
  padding: 0.25rem 0.4rem;
  background: #000f27;
  border: 1px solid #32476c;
  border-radius: 6px;
  transition: border-color 0.4s, background 0.4s, box-shadow 0.4s;
}
.summary-hw-lit {
  border-color: #b1c7f3;
  background: #000f27;
  box-shadow: 0 0 15px rgba(177,199,243,0.15);
}
.summary-hw-icon {
  color: #778cb5;
  transition: color 0.4s;
}
.summary-hw-lit .summary-hw-icon {
  color: #b1c7f3;
}
.summary-hw-name {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.45rem;
  font-weight: 700;
  color: #778cb5;
  transition: color 0.4s;
}
.summary-hw-lit .summary-hw-name {
  color: #b1c7f3;
}

/* ===== CHECKS ===== */
.summary-checks {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  justify-content: center;
}
.sum-check {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.55rem;
  font-weight: 600;
  color: #ccc;
  display: flex;
  align-items: center;
  gap: 0.2rem;
  opacity: 0;
  animation: sfadeIn 0.5s ease-out 4.0s both;
}
.sum-check:nth-child(2) { animation-delay: 4.2s; }
.sum-check:nth-child(3) { animation-delay: 4.4s; }
.sum-check-icon {
  color: #009d8d;
  font-weight: 900;
  font-size: 0.7rem;
  text-shadow: 0 0 8px rgba(0,157,141,0.4);
}

/* ===== MOTTO ===== */
.summary-motto {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.95rem;
  font-weight: 700;
  opacity: 0;
  transition: opacity 0.6s;
}
.summary-motto-show {
  opacity: 1;
}
.summary-motto-code {
  color: #778cb5;
}
.summary-motto-em {
  color: #009d8d;
  text-shadow: 0 0 15px rgba(0,157,141,0.3);
}

/* ===== FINAL BRAND ===== */
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
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 2.2rem;
  font-weight: 900;
  color: #009d8d;
  text-shadow: 0 0 40px rgba(0,157,141,0.6), 0 0 80px rgba(0,157,141,0.3), 0 0 120px rgba(0,157,141,0.1);
  letter-spacing: 0.2em;
  animation: sglowPulse 2s ease-in-out infinite;
}
.summary-final-tag {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.55rem;
  font-weight: 600;
  color: #778cb5;
  letter-spacing: 0.15em;
}

/* ===== TRANSITIONS ===== */
.sum-glow-enter-active {
  animation: sglowIn 0.8s ease-out;
}
.sum-glow-leave-active {
  animation: sglowIn 0.4s ease-in reverse;
}
.sum-fade-enter-active {
  transition: opacity 0.5s;
}
.sum-fade-leave-active {
  transition: opacity 0.3s;
}
.sum-fade-enter-from,
.sum-fade-leave-to {
  opacity: 0;
}

/* ===== KEYFRAMES ===== */
@keyframes sfadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes sstreamFlow {
  from { left: -5%; }
  to   { left: 105%; }
}
@keyframes sdotPulse {
  0%,100% { opacity: 0.4; transform: scale(0.8); }
  50%     { opacity: 1; transform: scale(1.3); }
}
@keyframes sglowIn {
  from { opacity: 0; transform: scale(0.5); }
  to   { opacity: 1; transform: scale(1); }
}
@keyframes sglowPulse {
  0%,100% { text-shadow: 0 0 40px rgba(0,157,141,0.6), 0 0 80px rgba(0,157,141,0.3); }
  50%     { text-shadow: 0 0 60px rgba(0,157,141,0.8), 0 0 120px rgba(0,157,141,0.4); }
}
</style>
