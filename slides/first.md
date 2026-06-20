---
layout: center
---

<div class="scale">
  <div class="beam">
    <div class="knob left-knob"></div>
    <div class="knob right-knob"></div>
    <div class="label left-label">Performance</div>
    <div class="label right-label">Lesbarkeit</div>
  </div>
  <div class="pivot"></div>
  <div class="pillar"></div>
  <div class="base"></div>
</div>

<div class="caption">
  Nullsummenspiel: Mehr Gewicht auf der einen Seite bedeutet weniger auf der anderen.
</div>

<style>
.scale {
  position: relative;
  width: 520px;
  height: 320px;
  margin: 0 auto;
}

/* === BASE (small triangle, sits at bottom) === */
.base {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 0;
  border-left: 24px solid transparent;
  border-right: 24px solid transparent;
  border-bottom: 14px solid #32476c;
}

/* === PILLAR (short, 1/4 of before) === */
.pillar {
  position: absolute;
  top: 253px;
  left: 50%;
  transform: translateX(-50%);
  width: 6px;
  height: 53px;
  background: #0b2447;
  border-radius: 2px;
}

/* === PIVOT (triangle pointing up) === */
.pivot {
  position: absolute;
  top: 238px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 0;
  border-left: 10px solid transparent;
  border-right: 10px solid transparent;
  border-bottom: 15px solid #fea619;
  z-index: 2;
}

/* === BEAM (flat, centered on pivot tip) === */
.beam {
  position: absolute;
  left: 40px;
  right: 40px;
  top: 234px;
  height: 8px;
  background: #778cb5;
  border-radius: 4px;
  transform-origin: center center;
  z-index: 3;
  animation: beamWobble 2.5s ease-in-out infinite;
}

/* === KNOBS (beam ends) === */
.knob {
  position: absolute;
  width: 16px;
  height: 16px;
  top: 50%;
  transform: translateY(-50%);
  background: #0b2447;
  border-radius: 50%;
  border: 1.5px solid #32476c;
}
.left-knob { left: -8px; }
.right-knob { right: -8px; }

/* === LABELS === */
.label {
  position: absolute;
  top: -36px;
  padding: 5px 18px;
  font-size: 1rem;
  font-weight: 700;
  border-radius: 16px;
  letter-spacing: 0.5px;
  white-space: nowrap;
  z-index: 10;
}

.left-label {
  left: 20px;
  background: #fea619;
  color: #fff;
}

.right-label {
  right: 20px;
  background: #009d8d;
  color: #fff;
}

/* === WOBBLE ANIMATION === */
@keyframes beamWobble {
  0%, 100% { transform: rotate(-5deg); }
  50%      { transform: rotate(5deg); }
}

/* === CAPTION === */
.caption {
  margin-top: 1rem;
  text-align: center;
  color: #74777f;
  font-size: 1rem;
  font-style: italic;
}
</style>
