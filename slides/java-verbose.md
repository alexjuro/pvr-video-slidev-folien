---
layout: center
---

<div v-click="1" class="snail-wrap">
  <span class="snail-icon">🐌</span>
  <span class="snail-label">Boilerplate</span>
</div>

```java
double[] results = new double[data.length];
for (int i = 0; i < data.length; i++) {
    results[i] = Math.sin(data[i]);
}
```

<style>
/* === SNAIL === */
.snail-wrap {
  position: fixed;
  right: 10%;
  top: 8.2rem;
  display: flex;
  align-items: center;
  gap: 0.4rem;
  z-index: 5;
}

.snail-icon {
  font-size: 2rem;
}

.snail-label {
  font-family: 'JetBrains Mono', 'Fira Code', monospace;
  font-size: 0.8rem;
  font-weight: 700;
  color: #ba1a1a;
  text-transform: uppercase;
  letter-spacing: 1px;
}
</style>
