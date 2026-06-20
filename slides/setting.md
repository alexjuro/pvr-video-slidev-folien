---
layout: center
---

<div class="simd-container">

  <!-- === TITLE === -->
  <div class="simd-label">SIMD</div>

  <!-- === INSTRUCTION REGISTER === -->
  <div class="instr-box">
    <span class="instr-text">MUL *</span>
  </div>
  <div class="instr-label">Single Instruction</div>

  <!-- === ARROW === -->
  <div class="simd-arrow">↓</div>

  <!-- === DATA REGISTERS (4 LANES) === -->
  <div class="lanes">
    <div class="pixel-box">P<sub>1</sub></div>
    <div class="pixel-box">P<sub>2</sub></div>
    <div class="pixel-box">P<sub>3</sub></div>
    <div class="pixel-box">P<sub>4</sub></div>
  </div>

  <div class="data-label">Multiple Data</div>

  <div class="cycle-note">Ein Taktzyklus</div>
</div>

<span class="ref">[3]</span>

<style>
.simd-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.4rem;
}

/* === SIMD HEADLINE === */
.simd-label {
  font-size: 3rem;
  font-weight: 900;
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  color: #b1c7f3;
  margin-bottom: 0.5rem;
}

/* === INSTRUCTION REGISTER === */
.instr-box {
  width: 120px;
  height: 52px;
  background: #000f27;
  border: 1.5px solid #32476c;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.instr-text {
  font-size: 1.8rem;
  font-weight: 800;
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  color: #fea619;
}

.instr-label {
  font-size: 0.8rem;
  color: #fea619;
  font-weight: 600;
  letter-spacing: 0.1em;
  margin-bottom: 0.2rem;
}

/* === ARROW === */
.simd-arrow {
  font-size: 1.6rem;
  color: #b1c7f3;
  line-height: 1;
}

/* === DATA REGISTER LANES === */
.lanes {
  display: flex;
  gap: 0.6rem;
  margin-top: 0.3rem;
}

/* === PIXEL BOXES === */
.pixel-box {
  width: 56px;
  height: 44px;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1rem;
  font-weight: 700;
  color: #ffffff;
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
}

.data-label {
  font-size: 0.8rem;
  color: #b1c7f3;
  font-weight: 600;
  letter-spacing: 0.1em;
}

/* === CYCLE NOTE === */
.cycle-note {
  margin-top: 0.6rem;
  font-size: 1rem;
  font-weight: 700;
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  color: #009d8d;
}

.ref {
  position: fixed;
  bottom: 1rem;
  right: 1.5rem;
  font-size: 0.8rem;
  color: #999;
}
</style>
