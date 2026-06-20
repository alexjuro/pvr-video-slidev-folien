---
layout: center
---

<div class="jvm-slide">
  <div class="logo-wrapper">
    <div class="glow"></div>
    <img src="/assets/jvm.png" class="jvm-logo" />
  </div>
  <p class="subtitle">Java Virtual Machine</p>
  <p class="tagline">Stabilität &amp; Leistung</p>
</div>

<span class="ref">[2]</span>

<style>
.jvm-slide {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 1.5rem;
}

.logo-wrapper {
  position: relative;
  width: 225px;
  height: 225px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.jvm-logo {
  position: relative;
  z-index: 1;
  width: 225px;
  height: 225px;
}

.subtitle {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 2.8rem;
  color: #191c1e;
  margin: 0;
  font-weight: 900;
}

.tagline {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.85rem;
  color: #fea619;
  margin: 0;
  font-weight: 700;
}

.ref {
  position: fixed;
  bottom: 1rem;
  right: 1.5rem;
  font-size: 0.8rem;
  color: #999;
}

</style>
