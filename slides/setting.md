---
layout: center
---

<div class="simd-container">

  <!-- === TITLE === -->
  <div class="simd-label">SIMD</div>

  <!-- === INSTRUCTION REGISTER === -->
  <div class="instr-box">
    <span class="instr-text">MUP</span>
  </div>
  <div class="instr-label">Single Instruction</div>

  <!-- === ARROW === -->
  <div class="arrow-shaft"></div>

  <!-- === DATA REGISTERS (4 LANES) === -->
  <div class="lanes">
    <div class="lane">
      <div class="pixel-label">P<sub>1</sub></div>
      <div class="pixel-box" data-lane="1"></div>
    </div>
    <div class="lane">
      <div class="pixel-label">P<sub>2</sub></div>
      <div class="pixel-box" data-lane="2"></div>
    </div>
    <div class="lane">
      <div class="pixel-label">P<sub>3</sub></div>
      <div class="pixel-box" data-lane="3"></div>
    </div>
    <div class="lane">
      <div class="pixel-label">P<sub>4</sub></div>
      <div class="pixel-box" data-lane="4"></div>
    </div>
  </div>

  <div class="data-label">Multiple Data</div>

  <div class="cycle-note">Ein Taktzyklus</div>
</div>

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
  color: #00e5ff;
  text-shadow: 0 0 30px rgba(0, 229, 255, 0.5);
  letter-spacing: 0.3em;
  margin-bottom: 0.5rem;
}

/* === INSTRUCTION REGISTER === */
.instr-box {
  width: 120px;
  height: 52px;
  background: linear-gradient(145deg, #1a1a2e, #16213e);
  border: 2.5px solid #0f3460;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 0 15px rgba(15, 52, 96, 0.4);
}

.instr-text {
  font-size: 1.8rem;
  font-weight: 800;
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  color: #ffd700;
  text-shadow: 0 0 15px rgba(255, 215, 0, 0.6);
}

.instr-label {
  font-size: 0.8rem;
  color: #ffd700;
  font-weight: 600;
  letter-spacing: 0.1em;
  margin-bottom: 0.2rem;
}

/* === ARROW === */
.arrow-shaft {
  position: relative;
  width: 8px;
  height: 40px;
  background: #00e5ff;
  border-radius: 4px 4px 0 0;
  box-shadow: 0 0 12px rgba(0, 229, 255, 0.5);
}

.arrow-shaft::after {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 50%;
  transform: translateX(-50%);
  border-left: 8px solid transparent;
  border-right: 8px solid transparent;
  border-top: 10px solid #00e5ff;
}

/* === DATA REGISTER LANES === */
.lanes {
  display: flex;
  gap: 0.6rem;
  margin-top: 0.3rem;
}

.lane {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.2rem;
}

.pixel-label {
  font-size: 0.85rem;
  font-weight: 700;
  color: #a0a0b0;
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
}

.pixel-box {
  width: 52px;
  height: 48px;
  background: linear-gradient(145deg, #1a1a2e, #16213e);
  border: 2px solid #0f3460;
  border-radius: 6px;
  box-shadow: 0 0 10px rgba(15, 52, 96, 0.3);
  position: relative;
}

.pixel-box::before {
  content: '';
  position: absolute;
  inset: 4px;
  border-radius: 3px;
}

.pixel-box[data-lane="1"]::before { background: rgba(0, 229, 255, 0.15); }
.pixel-box[data-lane="2"]::before { background: rgba(0, 229, 255, 0.25); }
.pixel-box[data-lane="3"]::before { background: rgba(0, 229, 255, 0.15); }
.pixel-box[data-lane="4"]::before { background: rgba(0, 229, 255, 0.25); }

.data-label {
  font-size: 0.8rem;
  color: #00e5ff;
  font-weight: 600;
  letter-spacing: 0.1em;
}

/* === CYCLE NOTE === */
.cycle-note {
  margin-top: 0.6rem;
  font-size: 1rem;
  font-weight: 700;
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  color: #39ff14;
  text-shadow: 0 0 15px rgba(57, 255, 20, 0.4);
}
</style>
