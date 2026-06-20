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
    <span class="op-op">→</span>
    <span class="op-factor">normFactor = 2.0</span>
  </div>

```java
normalizedWeights = weights ^ / normFactor
```

  <div v-click="1" class="op-sub">Präziser Einzeiler</div>

  <!-- === PARALLEL ARROWS (from ^ to each cell) === -->
  <div class="op-beams-outer">
    <div v-click="2" class="op-beam-trigger"></div>
    <div class="op-beams">
      <div class="op-beam">
        <span class="op-beam-cell">0.25</span>
        <div class="op-beam-bar"></div>
        <span class="op-beam-sign">/&nbsp;2.0</span>
      </div>
      <div class="op-beam">
        <span class="op-beam-cell">0.88</span>
        <div class="op-beam-bar"></div>
        <span class="op-beam-sign">/&nbsp;2.0</span>
      </div>
      <div class="op-beam">
        <span class="op-beam-cell">0.12</span>
        <div class="op-beam-bar"></div>
        <span class="op-beam-sign">/&nbsp;2.0</span>
      </div>
      <div class="op-beam">
        <span class="op-beam-cell">0.47</span>
        <div class="op-beam-bar"></div>
        <span class="op-beam-sign">/&nbsp;2.0</span>
      </div>
    </div>
  </div>

  <!-- === HW FOOTER === -->
  <div v-click="3" class="op-hw">Hardware-SIMD</div>

</div>

<span class="ref">[3, 4]</span>

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
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #ffffff;
}

.op-op {
  color: #b1c7f3;
  font-size: 1.2rem;
  opacity: 0.5;
}

.op-factor {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #009d8d;
}

.op-sub {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.8rem;
  font-weight: 400;
  color: #999;
  letter-spacing: 0.15em;
  animation: opIn 0.4s ease-out 0.1s both;
}

/* === BEAMS (parallel division arrows) === */
.op-beams-outer {
  position: relative;
}
.op-beam-trigger {
  position: absolute;
  pointer-events: none;
  opacity: 0;
  width: 0;
  height: 0;
}
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
  animation-play-state: paused;
}
.op-beams-outer:has(.op-beam-trigger:not(.slidev-vclick-hidden)) .op-beam {
  animation-play-state: running;
}
.op-beam:nth-child(1) { animation-delay: 0.05s; }
.op-beam:nth-child(2) { animation-delay: 0.15s; }
.op-beam:nth-child(3) { animation-delay: 0.25s;  }
.op-beam:nth-child(4) { animation-delay: 0.35s; }

.op-beam-cell {
  width: 56px;
  height: 40px;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #ffffff;
}

.op-beam-bar {
  width: 2px;
  height: 28px;
  background: linear-gradient(to bottom, #009d8d, #b1c7f3);
  border-radius: 1px;
  transform-origin: top center;
  transform: scaleY(0);
  animation: beamGrow 0.4s ease-out forwards;
  animation-play-state: paused;
}
.op-beams-outer:has(.op-beam-trigger:not(.slidev-vclick-hidden)) .op-beam-bar {
  animation-play-state: running;
}
.op-beam:nth-child(1) .op-beam-bar { animation-delay: 0.1s; }
.op-beam:nth-child(2) .op-beam-bar { animation-delay: 0.2s; }
.op-beam:nth-child(3) .op-beam-bar { animation-delay: 0.3s;  }
.op-beam:nth-child(4) .op-beam-bar { animation-delay: 0.4s; }

.op-beam-sign {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #009d8d;
  opacity: 0.7;
}

/* === HW FOOTER === */
.op-hw {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.85rem;
  font-weight: 700;
  color: #778cb5;
  letter-spacing: 0.2em;
  opacity: 0;
  animation: opIn 0.5s ease-out 0.1s both;
}

/* === KEYFRAMES === */
@keyframes opIn {
  from { opacity: 0; transform: translateY(8px); }
  to   { opacity: 1; transform: translateY(0); }
}


@keyframes beamGrow {
  to { transform: scaleY(1); }
}

.ref {
  position: fixed;
  bottom: 1rem;
  right: 1.5rem;
  font-size: 0.8rem;
  color: #999;
}
</style>
