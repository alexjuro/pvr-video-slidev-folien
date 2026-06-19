---
layout: center
---

<div class="mtw">

  <!-- LEFT: Code -->
  <div class="mtw-col">
    <div class="mtw-label">Code</div>
    <pre class="slidev-code"><code class="language-java">for(elem:elements){ process(elem); }</code></pre>
    <div class="mtw-arrow">&rarr;</div>
  </div>

  <!-- CENTER: Wall + Package -->
  <div class="mtw-col mtw-wall-col">
    <!-- Wall -->
    <div class="mtw-wall">
      <div class="mtw-wall-inner">
        <div class="mtw-wall-text">Betriebssystem / Kernel-Modus</div>
      </div>
    </div>
    <!-- Animated package area -->
    <div class="mtw-lift">
      <div class="mtw-pack">
        <div class="mtw-pack-label">Thread-Kontext<br/>Stack Frame</div>
        <div class="mtw-watch">⏱</div>
      </div>
    </div>
    <!-- Guide line -->
    <div class="mtw-guide"></div>
  </div>

  <!-- RIGHT: CPU -->
  <div class="mtw-col">
    <div class="mtw-label">Hardware</div>
    <div class="mtw-cpu">
      <div class="mtw-cpu-head">CPU</div>
      <div class="mtw-cores">
        <div class="mtw-core">Kern 1</div>
        <div class="mtw-core">Kern 2</div>
        <div class="mtw-core">Kern 3</div>
        <div class="mtw-core">Kern 4</div>
      </div>
    </div>
  </div>

</div>

<style>
.mtw {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  width: 100%;
  height: 380px;
  position: relative;
}
.mtw-col {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.6rem;
}
.mtw-wall-col {
  position: relative;
  width: 140px;
}
.mtw-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  font-weight: 700;
  color: #74777f;
  letter-spacing: 0.2em;
  text-transform: uppercase;
}


.mtw-arrow {
  font-size: 1.3rem;
  color: #b1c7f3;
  opacity: 0.4;
}

/* Wall */
.mtw-wall {
  width: 50px;
  height: 300px;
  background: repeating-linear-gradient(135deg,#2a1a1a 0px,#2a1a1a 12px,#3a2020 12px,#3a2020 24px);
  border-left: 4px solid #5a2a2a;
  border-right: 4px solid #5a2a2a;
  border-radius: 4px;
  box-shadow: inset 0 0 20px rgba(255,0,0,0.15), 4px 0 15px rgba(0,0,0,0.3), -4px 0 15px rgba(0,0,0,0.3);
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  z-index: 2;
}
.mtw-wall-inner {
  display: flex;
  align-items: center;
  justify-content: center;
}
.mtw-wall-text {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.7rem;
  font-weight: 700;
  color: #cc4444;
  text-shadow: 0 0 10px rgba(204,68,68,0.3);
  letter-spacing: 0.1em;
  writing-mode: sideways-lr;
}

/* Guide line */
.mtw-guide {
  position: absolute;
  left: 50%;
  top: 50%;
  width: 80px;
  height: 280px;
  margin-left: -40px;
  margin-top: -140px;
  border: 2px dashed #32476c;
  border-radius: 50%;
  opacity: 0.3;
  pointer-events: none;
  z-index: 0;
}

/* Lift track */
.mtw-lift {
  position: absolute;
  left: 50%;
  top: 50%;
  width: 0;
  height: 0;
  z-index: 3;
  pointer-events: none;
}

/* Package */
.mtw-pack {
  position: absolute;
  width: 130px;
  height: 60px;
  margin-left: -65px;
  margin-top: -30px;
  animation: mtwOrbit 4s ease-in-out infinite;
}
.mtw-pack-label {
  padding: 0.4rem 0.5rem;
  background: linear-gradient(145deg,#2a1a1a,#3a2020);
  border: 2.5px solid #cc4444;
  border-radius: 6px;
  box-shadow: 0 0 20px rgba(204,68,68,0.2);
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.55rem;
  font-weight: 700;
  color: #ff7777;
  text-align: center;
  line-height: 1.4;
}
.mtw-pack-label::before {
  content: '';
  position: absolute;
  top: -8px;
  left: 50%;
  margin-left: -2px;
  width: 4px;
  height: 8px;
  background: #666;
  border-radius: 2px;
}
.mtw-watch {
  position: absolute;
  top: -20px;
  right: -16px;
  font-size: 1.3rem;
  animation: mtwTick 0.6s ease-in-out infinite;
  filter: drop-shadow(0 0 6px rgba(255,200,0,0.5));
}

/* CPU */
.mtw-cpu {
  padding: 0.8rem;
  background: linear-gradient(145deg,#000f27,#0b2447);
  border: 2px solid #32476c;
  border-radius: 12px;
  box-shadow: 0 0 25px rgba(177,199,243,0.08);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}
.mtw-cpu-head {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.9rem;
  font-weight: 800;
  color: #b1c7f3;
  letter-spacing: 0.2em;
  text-shadow: 0 0 15px rgba(177,199,243,0.3);
}
.mtw-cores {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.3rem;
}
.mtw-core {
  padding: 0.3rem 0.5rem;
  background: #000f27;
  border: 1px solid #32476c;
  border-radius: 6px;
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.6rem;
  font-weight: 600;
  color: #778cb5;
  text-align: center;
}

/* Keyframes */
@keyframes mtwOrbit {
  0%   { transform: translate(-60px, 100px); opacity: 0; }
  8%   { opacity: 1; }
  25%  { transform: translate(-60px, -30px); }
  40%  { transform: translate(-20px, -80px); }
  50%  { transform: translate(0px, -90px); }
  60%  { transform: translate(20px, -80px); }
  75%  { transform: translate(60px, -30px); }
  92%  { transform: translate(60px, 100px); opacity: 1; }
  100% { transform: translate(60px, 100px); opacity: 0; }
}
@keyframes mtwTick {
  0%,100% { transform: rotate(-10deg) scale(1); }
  25%     { transform: rotate(0deg) scale(1.15); }
  50%     { transform: rotate(10deg) scale(1); }
  75%     { transform: rotate(0deg) scale(1.15); }
}

.slidev-code {
  font-size: 1.3rem !important;
}
</style>
