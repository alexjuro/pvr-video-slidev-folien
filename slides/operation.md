---
layout: center
---

<div class="op-wrapper">

  <!-- === TOP: SHRUNKEN DATA === -->
  <div class="op-top">
    <div class="op-matrix">
      <span class="op-cell-mini">0.25</span>
      <span class="op-cell-mini">0.88</span>
      <span class="op-cell-mini">0.12</span>
      <span class="op-cell-mini">0.47</span>
    </div>
    <span class="op-op">&rarr;</span>
    <span class="op-factor">normFactor = 2.0</span>
  </div>

  <!-- === CODE BOX === -->
  <div class="op-code">
    <span class="op-v">normalizedWeights</span>
    <span class="op-punct"> = </span>
    <span class="op-v">weights</span>
    <span class="op-caret">^</span>
    <span class="op-punct"> / </span>
    <span class="op-v">normFactor</span>
  </div>

  <div class="op-sub">Präziser Einzeiler</div>

  <!-- === PARALLEL ARROWS (from ^ to each cell) === -->
  <div class="op-beams">
    <div class="op-beam">
      <span class="op-beam-cell">0.25</span>
      <div class="op-beam-bar op-b1"></div>
      <span class="op-beam-sign">/&nbsp;2.0</span>
    </div>
    <div class="op-beam">
      <span class="op-beam-cell">0.88</span>
      <div class="op-beam-bar op-b2"></div>
      <span class="op-beam-sign">/&nbsp;2.0</span>
    </div>
    <div class="op-beam">
      <span class="op-beam-cell">0.12</span>
      <div class="op-beam-bar op-b3"></div>
      <span class="op-beam-sign">/&nbsp;2.0</span>
    </div>
    <div class="op-beam">
      <span class="op-beam-cell">0.47</span>
      <div class="op-beam-bar op-b4"></div>
      <span class="op-beam-sign">/&nbsp;2.0</span>
    </div>
  </div>

  <!-- === HW FOOTER === -->
  <div class="op-hw">Hardware-SIMD</div>

</div>

<style>
.op-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.4rem;
  height: 440px;
  position: relative;
}

/* === TOP ROW === */
.op-top {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  opacity: 0.6;
  font-size: 0.75rem;
}

.op-matrix {
  display: flex;
  gap: 0.25rem;
}

.op-cell-mini {
  width: 48px;
  height: 34px;
  background: linear-gradient(145deg, #1a1a2e, #16213e);
  border: 1.5px solid #0f3460;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.65rem;
  font-weight: 600;
  color: #c0c0d0;
}

.op-op {
  color: #00e5ff;
  font-size: 1.2rem;
  opacity: 0.5;
}

.op-factor {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.65rem;
  color: #39ff14;
}

/* === CODE BOX === */
.op-code {
  padding: 0.7rem 1.4rem;
  background: linear-gradient(145deg, #1a1a2e, #16213e);
  border: 2px solid #0f3460;
  border-radius: 10px;
  box-shadow: 0 0 30px rgba(0, 229, 255, 0.15);
  display: flex;
  align-items: center;
  gap: 0.15rem;
  animation: opIn 0.5s ease-out both;
}

.op-v {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 1.25rem;
  font-weight: 700;
  color: #e0e0e0;
}

.op-punct {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 1.25rem;
  font-weight: 700;
  color: #5a5a7a;
}

.op-caret {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 1.45rem;
  font-weight: 900;
  color: #39ff14;
  text-shadow: 0 0 20px rgba(57, 255, 20, 0.8), 0 0 40px rgba(57, 255, 20, 0.4);
  animation: pulseGlow 1.5s ease-in-out infinite;
}

.op-sub {
  font-size: 0.8rem;
  font-weight: 600;
  color: #5a5a7a;
  letter-spacing: 0.15em;
  animation: opIn 0.5s ease-out 0.3s both;
}

/* === BEAMS (parallel division arrows) === */
.op-beams {
  display: flex;
  gap: 0.5rem;
  margin-top: 0.2rem;
}

.op-beam {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.2rem;
  opacity: 0;
  animation: opIn 0.5s ease-out forwards;
}
.op-beam:nth-child(1) { animation-delay: 0.5s; }
.op-beam:nth-child(2) { animation-delay: 0.65s; }
.op-beam:nth-child(3) { animation-delay: 0.8s;  }
.op-beam:nth-child(4) { animation-delay: 0.95s; }

.op-beam-cell {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.75rem;
  font-weight: 700;
  color: #ffd700;
  text-shadow: 0 0 8px rgba(255, 215, 0, 0.3);
}

.op-beam-bar {
  width: 2px;
  height: 28px;
  background: linear-gradient(to bottom, #39ff14, #00e5ff);
  border-radius: 1px;
  box-shadow: 0 0 6px rgba(57, 255, 20, 0.5);
  animation: beamGrow 0.4s ease-out forwards;
  transform-origin: top center;
  transform: scaleY(0);
}
.op-b1 { animation-delay: 0.6s; }
.op-b2 { animation-delay: 0.75s; }
.op-b3 { animation-delay: 0.9s;  }
.op-b4 { animation-delay: 1.05s; }

.op-beam-sign {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.6rem;
  font-weight: 600;
  color: #39ff14;
  opacity: 0.7;
}

/* === HW FOOTER === */
.op-hw {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.85rem;
  font-weight: 700;
  color: #00e5ff;
  text-shadow: 0 0 15px rgba(0, 229, 255, 0.4);
  letter-spacing: 0.2em;
  opacity: 0;
  animation: opIn 0.8s ease-out 1.5s both;
}

/* === KEYFRAMES === */
@keyframes opIn {
  from { opacity: 0; transform: translateY(8px); }
  to   { opacity: 1; transform: translateY(0); }
}

@keyframes pulseGlow {
  0%, 100% { text-shadow: 0 0 20px rgba(57, 255, 20, 0.8), 0 0 40px rgba(57, 255, 20, 0.4); }
  50%      { text-shadow: 0 0 30px rgba(57, 255, 20, 1.0), 0 0 60px rgba(57, 255, 20, 0.6); }
}

@keyframes beamGrow {
  to { transform: scaleY(1); }
}
</style>
