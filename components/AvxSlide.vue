<template>
  <div class="avx">
    <!-- TITLE -->
    <div class="avx-title-group">
      <div class="avx-title">AVX</div>
      <div class="avx-sub">Advanced Vector Extensions</div>
    </div>

    <!-- REGISTER -->
    <div class="avx-reg">
      <div class="avx-reg-label">512-Bit Register</div>

      <div class="avx-lanes">
        <!-- Lane 1 -->
        <div class="avx-lane">
          <div class="avx-arr">←</div>
          <div class="avx-cell">
            <span class="avx-val">0.25</span>
            <span class="avx-type">float64</span>
          </div>
          <div class="avx-slot"></div>
        </div>
        <!-- Lane 2 -->
        <div class="avx-lane">
          <div class="avx-arr">←</div>
          <div class="avx-cell">
            <span class="avx-val">0.88</span>
            <span class="avx-type">float64</span>
          </div>
          <div class="avx-slot"></div>
        </div>
        <!-- Lane 3 -->
        <div class="avx-lane">
          <div class="avx-arr">←</div>
          <div class="avx-cell">
            <span class="avx-val">0.12</span>
            <span class="avx-type">float64</span>
          </div>
          <div class="avx-slot"></div>
        </div>
        <!-- Lane 4 -->
        <div class="avx-lane">
          <div class="avx-arr">←</div>
          <div class="avx-cell">
            <span class="avx-val">0.47</span>
            <span class="avx-type">float64</span>
          </div>
          <div class="avx-slot"></div>
        </div>
      </div>

      <!-- Arrow through all lanes -->
      <div class="avx-strike">
        <div class="avx-strike-arrow">↓</div>
        <div class="avx-strike-label">1 Taktzyklus</div>
      </div>
    </div>

    <!-- CONCLUSION -->
    <div class="avx-fazit">100% Hardware · 0% OS-Overhead</div>
  </div>
</template>

<style scoped>
.avx {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 1.2rem;
  width: 100%;
}

/* ===== TITLE ===== */
.avx-title-group {
  text-align: center;
  animation: avxFadeIn 0.6s ease-out both;
}
.avx-title {
  font-size: 4rem;
  font-weight: 900;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #b1c7f3;
  letter-spacing: 0.25em;
  line-height: 1.1;
}
.avx-sub {
  font-size: 0.9rem;
  font-weight: 600;
  color: #778cb5;
  letter-spacing: 0.15em;
  margin-top: 0.2rem;
}

/* ===== REGISTER ===== */
.avx-reg {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  padding: 0.8rem 1.5rem 1.2rem;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 12px;
  animation: avxFadeIn 0.6s ease-out 0.3s both;
}
.avx-reg-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  font-weight: 700;
  color: #fea619;
  letter-spacing: 0.15em;
}

/* ===== LANES ===== */
.avx-lanes {
  display: flex;
  gap: 0.25rem;
}
.avx-lane {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  position: relative;
}

/* Arrow flying in */
.avx-arr {
  font-size: 1.8rem;
  font-weight: 300;
  color: #b1c7f3;
  opacity: 0;
  transform: translateX(-30px);
  animation: avxFlyIn 0.5s ease-out forwards;
}
.avx-lane:nth-child(1) .avx-arr { animation-delay: 0.8s; }
.avx-lane:nth-child(2) .avx-arr { animation-delay: 0.9s; }
.avx-lane:nth-child(3) .avx-arr { animation-delay: 1.0s; }
.avx-lane:nth-child(4) .avx-arr { animation-delay: 1.1s; }

/* Value cell */
.avx-cell {
  width: 80px;
  padding: 0.4rem 0;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.15rem;
  opacity: 0;
  transform: translateX(-20px);
  animation: avxFlyIn 0.4s ease-out forwards;
}
.avx-lane:nth-child(1) .avx-cell { animation-delay: 1.0s; }
.avx-lane:nth-child(2) .avx-cell { animation-delay: 1.1s; }
.avx-lane:nth-child(3) .avx-cell { animation-delay: 1.2s; }
.avx-lane:nth-child(4) .avx-cell { animation-delay: 1.3s; }

.avx-val {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 1.1rem;
  font-weight: 700;
  color: #ffffff;
}
.avx-type {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.5rem;
  font-weight: 700;
  color: #fea619;
}

/* Slot gaps between lanes */
.avx-slot {
  width: 4px;
  height: 70px;
  background: #32476c;
  opacity: 0.5;
  position: absolute;
  right: -4px;
  top: 0;
}
.avx-lane:last-child .avx-slot { display: none; }

/* ===== STRIKE ARROW ===== */
.avx-strike {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.1rem;
  opacity: 0;
  animation: avxFadeIn 0.5s ease-out 2.0s both;
}
.avx-strike-arrow {
  font-size: 2.2rem;
  font-weight: 900;
  color: #009d8d;
  animation: avxPulse 1.2s ease-in-out infinite;
  line-height: 1;
}
.avx-strike-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.85rem;
  font-weight: 700;
  color: #009d8d;
  letter-spacing: 0.1em;
}

/* ===== CONCLUSION ===== */
.avx-fazit {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 1.4rem;
  font-weight: 900;
  color: #009d8d;
  letter-spacing: 0.05em;
  text-align: center;
  opacity: 0;
  animation: avxFadeIn 0.8s ease-out 2.8s both;
}

/* ===== KEYFRAMES ===== */
@keyframes avxFadeIn {
  from { opacity: 0; transform: translateY(12px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes avxFlyIn {
  from { opacity: 0; transform: translateX(-30px); }
  to   { opacity: 1; transform: translateX(0); }
}
@keyframes avxPulse {
  0%,100% { transform: scale(1); opacity: 1; }
  50%     { transform: scale(1.15); opacity: 0.85; }
}
</style>
