---
title: Tricks to get extended precision in Julia/Matlab
summary: A short blurb on how extended precision can be achieved in Julia and Matlab.
date: 2025-04-14
authors:
  - admin
tags:
  - Matlab
  - Julia
  - Code

---


In many scientific and engineering applications, double-precision floating point (i.e., `Float64`) is insufficient for achieving the desired level of accuracy. This is especially true in simulations involving extreme scales, such as black hole perturbation theory or gravitational wave modeling, where small numerical errors can propagate and dominate the result. Here are some **tricks and tools** to achieve **extended precision** in **Julia** and **MATLAB**, with examples from my own research experience.

---

## 🔬 Why Extended Precision?

- **Round-off errors** can dominate in long-time evolutions or chaotic systems.
- **Condition numbers** in linear systems can lead to significant loss of accuracy.
- **Waveform modeling** for gravitational waves often requires more than 16 decimal digits to preserve phase accuracy.

---

## 🟣 Extended Precision in Julia

Julia has several powerful packages that enable arbitrary or extended precision:

### 1. `BigFloat` (Arbitrary Precision)

```julia
setprecision(BigFloat, 256)  # Set global precision
x = BigFloat("1.234567890123456789")
```

**Pros:** Native to Julia, integrates with most libraries.

**Cons:** Slower due to arbitrary precision overhead.

### 2. `MultiFloats.jl` (Quad/Octo Precision)

MultiFloats uses a technique called **compensated arithmetic**, representing numbers as tuples of standard `Float64`s:

```julia
using MultiFloats
const T = Float64x2  # Roughly quad precision
x = T(1.2345678901234567)
y = T(1.0000000000000001)
z = x + y
```

**Pros:**
- Significantly faster than `BigFloat`
- Easily supports `Float64x2`, `Float64x3`, etc.
- Great for simulations where **precision > speed**, but **not arbitrary precision**

**Cons:**
- Not universally compatible with every Julia library.
- Requires careful variable type management.

### 3. Hardware-Supported Quad Precision (Power9 etc.)
If you’re on specialized hardware like IBM Power9:
- You can access hardware quad-precision through libraries like `libquadmath` (though Julia does not natively expose it yet).
- Use with C wrappers or special packages (still under development).

---

## 🟡 Extended Precision in MATLAB

MATLAB does not support extended precision out of the box, but there are options:

### 1. `vpa` (Symbolic Math Toolbox)

```matlab
digits(34)  % Roughly quadruple precision
x = vpa('1.234567890123456789')
```

**Pros:** Easy to use, adjustable precision.

**Cons:** Slow; not intended for full PDE solvers or high-performance work.

### 2. Using External Libraries: `DoubleDouble`

One option is the open-source [DoubleDouble](https://github.com/tholden/DoubleDouble) library:

Steps:
1. Download the `DoubleDouble` files and add to your path.
2. Use `dd` type:

```matlab
x = dd(1.2345678901234567);
y = dd(1.0000000000000001);
z = x + y;
```

**Pros:** Near `Float64x2` behavior.

**Cons:** Manual management, can’t use with built-in solvers easily.

---

## 🧪 My Use Case: Gravitational Wave Solvers

In solving the Teukolsky equation using discontinuous Galerkin methods, I found that round-off error polluted late-time tails and memory effects. Switching to `Float64x2` in Julia gave me clean, smooth decay curves and more reliable waveform extraction. It’s a small change, but the numerical impact was enormous.

---

## 🧠 Tips

- **Track all constants**: Don’t forget to convert literals and constants to extended precision manually.
- **Use type annotations**: Especially in Julia—otherwise you risk automatic down-casting.
- **Benchmark!**: Sometimes `Float64x2` is just enough, and you don’t need full `BigFloat`.

---

## 🧵 Related Tools
- Julia: `ArbNumerics.jl`, `DoubleFloats.jl`
- MATLAB: [Advanpix Multiprecision Toolbox](https://www.advanpix.com/)

---

## 🚀 Conclusion

Extended precision is not just a luxury—it’s a **requirement** in certain scientific domains. Whether you're building waveform surrogates or simulating relativistic particles, understanding and deploying these tools can help you **unlock cleaner, more accurate simulations**.

Got more tricks? [Message me](mailto:mvishal@umassd.edu) or connect on GitHub!

---

**Keywords:** Julia, MATLAB, BigFloat, Float64x2, MultiFloats, vpa, extended precision, DoubleDouble, gravitational wave modeling, discontinuous Galerkin.
