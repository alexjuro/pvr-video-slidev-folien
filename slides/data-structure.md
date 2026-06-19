---
layout: center
---

<div class="ds9">
  <div class="ds9-nn"></div>
  <div class="ds9-title">Datenstruktur</div>
  <div class="ds9-body">
    <div class="ds9-left">
      <div class="ds9-lbl">weights</div>
      <div class="ds9-grid">
        <span class="ds9-cell">0.25</span>
        <span class="ds9-cell">0.88</span>
        <span class="ds9-cell">0.12</span>
        <span class="ds9-cell">0.47</span>
      </div>
    </div>
    <span class="ds9-arr">→</span>
    <div class="ds9-right">
      <span class="ds9-lbl">normFactor</span>
      <span class="ds9-val">2.0</span>
    </div>
  </div>
</div>

<style>
.ds9 {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.ds9-title {
  font-size: 2.5rem;
  font-weight: 900;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  color: #b1c7f3;
  text-shadow: 0 0 30px rgba(11,36,71,0.5);
  letter-spacing: 0.08em;
}

.ds9-body {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.ds9-left, .ds9-right {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
}

.ds9-lbl {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  font-weight: 700;
  color: #778cb5;
  letter-spacing: 0.1em;
}

.ds9-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3px;
}

.ds9-cell {
  width: 60px;
  height: 40px;
  background: #000f27;
  border: 2px solid #32476c;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.85rem;
  font-weight: 700;
  color: #fea619;
}

.ds9-arr {
  font-size: 1.5rem;
  color: #b1c7f3;
  opacity: 0.6;
  align-self: center;
}

.ds9-val {
  width: 80px;
  height: 40px;
  background: #00120f;
  border: 2px solid #005048;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.85rem;
  font-weight: 700;
  color: #009d8d;
}
</style>
