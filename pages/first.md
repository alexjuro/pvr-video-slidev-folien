---
layout: center
---

# Performance vs. Lesbarkeit

<div class="scale-container">
  <div class="scale-base"></div>

  <div class="scale-beam">
    <div class="label left">Performance</div>
    <div class="label right">Lesbarkeit</div>
  </div>
</div>

<div class="caption">
  Nullsummenspiel: Mehr Gewicht auf der einen Seite bedeutet weniger auf der anderen.
</div>

<style>
.scale-container {
  position: relative;
  width: 700px;
  height: 320px;
  margin: 40px auto;
}

/* Standfuß */
.scale-base {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 20px;
  height: 180px;
  background: #666;
}

.scale-base::after {
  content: "";
  position: absolute;
  bottom: -12px;
  left: -70px;
  width: 160px;
  height: 12px;
  background: #666;
  border-radius: 6px;
}

/* Balken */
.scale-beam {
  position: absolute;
  left: 50%;
  top: 80px;
  width: 520px;
  height: 8px;
  background: #444;
  transform-origin: center center;
  animation: sway 4s ease-in-out infinite;
}

/* Mittelpunkt */
.scale-beam::before {
  content: "";
  position: absolute;
  left: 50%;
  top: -18px;
  transform: translateX(-50%);
  width: 0;
  height: 0;
  border-left: 22px solid transparent;
  border-right: 22px solid transparent;
  border-bottom: 40px solid #666;
}

.label {
  position: absolute;
  top: -55px;
  font-size: 1.3rem;
  font-weight: 700;
  white-space: nowrap;
}

.left {
  left: -30px;
}

.right {
  right: -30px;
}

@keyframes sway {
  0% {
    transform: translateX(-50%) rotate(-10deg);
  }
  50% {
    transform: translateX(-50%) rotate(10deg);
  }
  100% {
    transform: translateX(-50%) rotate(-10deg);
  }
}

.caption {
  margin-top: 2rem;
  text-align: center;
  opacity: 0.75;
  font-size: 1rem;
}
</style>
