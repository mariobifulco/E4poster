---
marp: true
theme: qsplit
size: A1
math: katex
paginate: false
title: 'QSplit: A Workflow-Oriented Hybrid Quantum–Classical Optimization Framework'
author: 'Mario Bifulco, Francesco Medina, Doriana Medić, Luca Roversi, Marco Aldinucci'
# description: 'A modular framework for decomposition, quantum optimization and aggregation.'
---

<div class="masthead">
<div class="brand">

![University of Turin](img/unito-logo.svg)

</div>
<div>

# <span class="project">QSplit</span><br>A Workflow-Oriented Hybrid<br>Quantum-Classical Optimization Framework

<p class="authors">Mario Bifulco, Francesco Medina, Doriana Medić, Luca Roversi, Marco Aldinucci</p>
<!-- <p class="affiliation">University of Turin - Department of Computer Science</p> -->

</div>
</div>

<div class="lead">

**QSplit in a nutshell**
QSplit enables quantum optimization beyond current QPU size through structure-aware decomposition, compact problem representations, and modular HPC-QPU integration.

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

### Problems outgrow QPUs

Real industrail optimization problems are much larger than current noisy QPUs

</div>
<div class="item">

### Workflow portability

Significant differences across quantum vendors require tailored approaches to orchestrate heterogeneous resources

</div>
</div>
<div class="block">

## <span class="num">02</span> Objectives

- **Scale the problem**: Study decomposition and aggregation techniques for large QUBO instances
- **HPC-Quantum integration**: Integrate quantum solvers efficiently into HPC optimization workflows, reducing classical-quantum data movement

</div>
<div class="block">

## <span class="num">03</span> Problem & data

**Quadratic Unconstrained Binary Optimization (QUBO)**

<div class="formula">

$$\min_{x\in\{0,1\}^{n}} x^{\mathsf T}Qx \footnotesize\qquad Q\in\mathbb{R}^{n\times n}, n\in \{0, 1\}$$

</div>

QSplit is **problem-agnostic**, supporting any problem formulated as a QUBO, while its performance depends on the **instance structure**, including coefficient sparsity, distribution, and magnitude

![sparse-dense](img/sparse_dense.svg)

</div>
</div>
<div class="column middle">
<div class="block">

## <span class="num">04</span> Methodology

### A modular split-solve-aggregate pipeline

QSplit allows a modular workflow tailored for optimization problems and orchestrated via **Streamflow** workflow management system.

<div class="workflow">

![Split-solve-aggregate workflow: input QUBO, split into subproblems (B), parallel CPU, GPU and QPU solvers (A), aggregate a global solution (B), and one-shot output (C). Ellipses indicate additional solvers.](img/workflow.svg)

</div>

<div class="method">

### <span class="letter">A</span> Quantum solvers

- **Fewer variational cycles**: Study QAOA parameterizations that reduce the number of classical-quantum optimization loops
- **HPC training + QC optimization**: Move QAOA parameter training to HPC resources and use quantum resources for optimization
- **Compact quantum encoding**: Pauli Correlation Encoding (PCE) represents logical QUBO variables through correlations over fewer qubits

<div class="pce-placeholder">
<p>

![PCE](img/pce.svg)

</p>
</div>
</div>
<div class="method">

### <span class="letter">B</span> Structure-aware pipeline

Structure-aware splitting methods aim to preserve as much information as possible in each subproblem, simplifying subsequent aggregation

</div>
<div class="method">

### <span class="letter">C</span> One-shot approach

QSplit currently uses single-pass optimization, aiming to find the best possible solution with minimal resource use

</div>
</div>
</div>
<div class="column">
<div class="block">

## <span class="num">05</span> Results

<div class="metrics">
<div class="metric-row">
<div class="metric">50x<span>Handled problems</span></div>
<div class="metric">- 99%<span>Variational loops</span></div>
</div>
<p>QSplit allows to optimize Max-Cut problems bigger than the QPU with a lightweight variational training with almost no performance drop</p>
</div>

<p><br>QSplit aims to reduce the size of each quantum task and the cost of its integration into the classical workflow</p>

<div class="comparison-placeholder">
<p>

![Quantum VS Classic](img/qvsc.svg)

</p>
</div>
</div>
<div class="block future">

## <span class="num">06</span> Future work

<div class="item">

### QOLC

Quadratic objectives with linear constraints: incorporate constraints into mixers

</div>
<div class="item">

### QUIO

Extend to Quadratic Unconstrained Integer Optimization to address a broader class of real-world problems

</div>
<div class="item">

### Refinement process

Provide an optional refinement process in order to balance resource consumption and quality solution

</div>
</div>

<div class="footer">

<div class="qr-links" aria-label="Project resources">
<div class="qr-resource">
<h3>
<img class="qr-icon" src="img/github.svg" alt="">
GitHub
</h3>
<div class="qr-code">
<img src="img/qr-github.png" alt="GitHub QR code">
</div>
</div>

<div class="qr-resource">
<h3>
<img class="qr-icon" src="img/paper.svg" alt="">
Paper
</h3>
<div class="qr-code">
<img src="img/qr-paper.png" alt="Paper QR code">
</div>
</div>
</div>

<div class="contact">
<h3>Contact</h3>
<div class="people">
<img src="img/Aldinucci.png" alt="">
<div class="contact-info">
<strong>TODO</strong>
<p>name.surname@unito.it</p>
</div>
</div>
</div>

</div>
</div>
</div>
