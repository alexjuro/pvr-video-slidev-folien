---
layout: center
---

<div class="slide-stack">

<div class="title-row">
  <div class="title-main">Implicit Vectorization</div>
</div>

<div v-click="1" class="iv-code-area">
  <div class="iv-scalar">

```java
y = sin(x)
```

  </div>

```java
y = sin(weights)
```

</div>

<ImplicitVecSlide />

<div v-click="3" class="iv-transpile">

```java
y = sin(weights^)
```

  <div class="iv-transpile-label">Compiler transpiliert zu:</div>
</div>

</div>

<style>
.iv-code-area {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}
.iv-scalar {
  opacity: 0.4;
}
.iv-transpile {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
}
.iv-transpile-label {
  font-family: 'JetBrains Mono','Fira Code',monospace;
  font-size: 0.65rem;
  font-weight: 700;
  color: #74777f;
  letter-spacing: 0.1em;
}
</style>
