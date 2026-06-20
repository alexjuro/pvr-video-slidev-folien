---
layout: center
---

<div class="ds9">
  <div class="ds9-lbl" style="grid-area: lbl-w">weights</div>
  <span class="ds9-lbl" style="grid-area: lbl-n">normFactor</span>

  <div class="ds9-grid" style="grid-area: grid">
    <span class="ds9-cell">0.25</span>
    <span class="ds9-cell">0.88</span>
    <span class="ds9-cell">0.12</span>
    <span class="ds9-cell">0.47</span>
  </div>
  <span class="ds9-arr" style="grid-area: arr">→</span>
  <span class="ds9-val" style="grid-area: val">2.0</span>
</div>

<style>
.ds9 {
  display: grid;
  grid-template-columns: auto 3rem auto;
  grid-template-rows: auto auto;
  grid-template-areas:
    "lbl-w .    lbl-n"
    "grid  arr  val";
  gap: 0.5rem 1.5rem;
  justify-items: center;
  align-items: center;
  transform: scale(1.35);
}

.ds9-lbl {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #fea619;
  letter-spacing: 0.1em;
}

.ds9-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 5px;
}

.ds9-cell {
  width: 80px;
  height: 56px;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #ffffff;
}

.ds9-arr {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  color: #b1c7f3;
  opacity: 0.6;
  line-height: 1;
}

.ds9-val {
  width: 110px;
  height: 56px;
  background: #0b2447;
  border: 1.5px solid #32476c;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #ffffff;
}
</style>
