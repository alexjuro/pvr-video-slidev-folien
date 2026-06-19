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

```java
normalizedWeights = weights ^ / normFactor
```

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
  background: linear-gradient(145deg, #000f27, #0b2447);
  border: 1.5px solid #32476c;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.65rem;
  font-weight: 600;
  color: #778cb5;
}

.op-op {
  color: #b1c7f3;
  font-size: 1.2rem;
  opacity: 0.5;
}

.op-factor {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.65rem;
  color: #009d8d;
}

.op-sub {
  font-size: 0.8rem;
  font-weight: 600;
  color: #74777f;
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
  color: #fea619;
  text-shadow: 0 0 8px rgba(254, 166, 25, 0.3);
}

.op-beam-bar {
  width: 2px;
  height: 28px;
  background: linear-gradient(to bottom, #009d8d, #b1c7f3);
  border-radius: 1px;
  box-shadow: 0 0 6px rgba(0, 157, 141, 0.5);
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
  color: #009d8d;
  opacity: 0.7;
}

/* === HW FOOTER === */
.op-hw {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.85rem;
  font-weight: 700;
  color: #b1c7f3;
  text-shadow: 0 0 15px rgba(177, 199, 243, 0.4);
  letter-spacing: 0.2em;
  opacity: 0;
  animation: opIn 0.8s ease-out 1.5s both;
}

/* === KEYFRAMES === */
@keyframes opIn {
  from { opacity: 0; transform: translateY(8px); }
  to   { opacity: 1; transform: translateY(0); }
}


@keyframes beamGrow {
  to { transform: scaleY(1); }
}

.slidev-code {
  font-size: 1.5rem !important;
}
</style>
