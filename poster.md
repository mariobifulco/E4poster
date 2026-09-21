---
marp: true
theme: qsplit
size: A1
math: katex
paginate: false
title: 'QSplit: Hybrid HPC-Quantum Workflows for Large-Scale QUBO Optimization'
author: 'Mario Bifulco, Francesco Medina, Doriana Medić, Luca Roversi, Marco Aldinucci'
# description: 'A modular framework for decomposition, quantum optimization and aggregation.'
---

<div class="masthead">
<div class="brand">

![University of Turin](img/unito-logo.svg)

</div>
<div>

# <span class="project">QSplit</span><br>Hybrid HPC-Quantum Workflows for Optimization

<p class="authors">Mario Bifulco, Francesco Medina, Doriana Medić, Luca Roversi, Marco Aldinucci</p>
<p class="affiliation">University of Turin - Department of Computer Science</p>

</div>
</div>

<div class="lead">

**Decompose. Optimize. Aggregate.**
QSplit combines structure-aware decomposition, compact quantum encodings and configurable pipelines to bring large-scale optimization into hybrid HPC-Quantum workflows

</div>

<div class="columns">
<div class="column">
<div class="block">

## <span class="num">01</span> Motivation

<div class="item">

### Quantum as an accelerator

Quantum computing can act as an accelerator inside HPC workflows

</div>
<div class="item">

### Communication has a cost

Hybrid performance depends on minimizing communication between classical and quantum resources

</div>
<div class="item">

### Problems outgrow QPUs

Real industrail optimization problems are much larger than current noisy QPUs

</div>
</div>
<div class="block">

## <span class="num">02</span> Objectives

<div class="callout">

### Scale the problem

Study decomposition and aggregation techniques for large QUBO instances

</div>
<div style="height:22px"></div>
<div class="callout">

### Streamline the workflow

Integrate quantum solvers efficiently into HPC optimization workflows, reducing classical-quantum interaction

</div>
</div>
<div class="block">

## <span class="num">03</span> Problem & data

**Quadratic Unconstrained Binary Optimization (QUBO)**

<div class="formula">

$$\min_{x\in\{0,1\}^{n}} x^{\mathsf T}Qx$$

<div class="small">

$Q\in\mathbb{R}^{n\times n}$, $n$ binary variables

</div>
</div>

QSplit is **problem-agnostic**: any problem expressed as a QUBO can enter the workflow

Performance depends on the **structure of the instance**, including sparsity, distribution and magnitude of its coefficients

<div class="placeholder data-placeholder">
<span class="ph-label">Placeholder - Dataset</span>
<strong>Sparse QUBO / dense QUBO</strong>
<p>Insert matrix plots and benchmark details</p>
</div>

</div>
</div>
<div class="column middle">
<div class="block">

## <span class="num">04</span> Methodology

### A modular split-solve-aggregate pipeline

Decompose the input, solve manageable subproblems and combine their solutions

<div class="workflow">
<div class="flow-step">Input QUBO</div>
<div class="arrow">↓</div>
<div class="flow-step red">Structure-aware split<span>Generate solver-compatible subproblems</span></div>
<div class="parallel">
<div class="arrow">↓</div>
<div class="arrow">↓</div>
</div>
<div class="parallel">
<div class="flow-step">Classical solvers<span>HPC resources</span></div>
<div class="flow-step">Quantum solvers<span>Quantum backends</span></div>
</div>
<div class="parallel">
<div class="arrow">↓</div>
<div class="arrow">↓</div>
</div>
<div class="flow-step gray">Aggregate<span>Reconstruct a global solution</span></div>
<div class="arrow">↓</div>
<div class="flow-step">Output solution</div>
</div>

<div class="method">

### <span class="letter">A</span> Compact quantum encoding

**Pauli Correlation Encoding (PCE)** represents logical QUBO variables through correlations over fewer qubits

<div class="placeholder pce-placeholder">
<p>

![PCE](img/pce.svg)

</p>
</div>
</div>
<div class="method">

### <span class="letter">B</span> Fewer variational cycles

Study QAOA parameterizations that reduce the number of classical-quantum optimization loops

</div>
<div class="method">

### <span class="letter">C</span> HPC training + QC optimization

Move QAOA training to HPC resources and use quantum resources for optimization, aiming to minimize costly communication

<div class="transfer"><span>HPC<br>Training</span><b>→</b><span>QC<br>Optimization</span></div>
</div>
</div>
</div>

<div class="column">
<div class="block">

## <span class="num">05</span> Results

<div class="metrics">
<div class="metric-row">
<div class="metric">???<span>QUBO variables</span></div>
<div class="metric">???<span>backend qubits</span></div>
</div>
<p>QSplit handles max-cut instances 10x the size of the QPU</p>
</div>

<p class="result-note"><strong>Structure-aware decomposition</strong> preserves solution quality better than conventional recursive strategies as problem size increases.</p>

<div class="placeholder results-placeholder">
<span class="ph-label">Placeholder - Results plot</span>
<strong>Solution quality<br>vs. problem size</strong>
<p>Compare structure-aware and recursive decomposition</p>
<p>Insert measured data,<br>legend and metric definition</p>
</div>

<div class="callout" style="margin-top:28px">

### Two complementary levers

Reduce the size of each quantum task **and** the cost of its integration into the classical workflow

</div>
</div>

<div class="placeholder comparison-placeholder">
<span class="ph-label">Placeholder - Pipeline comparison</span>
<strong>Structure-aware / recursive splitting</strong>
<p>Insert the comparative pipeline diagram</p>
</div>

<div class="block future">

## <span class="num">06</span> Future work

<div class="item">

### QOLC

Quadratic objectives with linear constraints: incorporate constraints into mixers, including a native Knapsack formulation

</div>
<div class="item">

### QUIO

Extend to Quadratic Unconstrained Integer Optimization to address a broader class of real-world problems

</div>
<div class="item">

### Exact optimization

Use quantum solvers as probabilistic subroutines within iterative classical optimization methods

</div>
</div>
</div>
</div>

<div class="footer">
<div>

### References

[PLACEHOLDER: QSplit paper / preprint]<br>
[PLACEHOLDER: PCE and QAOA references]

</div>
<div>

### Paper - Code - Contact

[PLACEHOLDER: repository / project URL]<br>
[PLACEHOLDER: contact email]

</div>
<div class="placeholder qr"><span class="ph-label">Placeholder</span><strong>QR code</strong></div>
</div>
