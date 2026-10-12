---
marp: true
theme: qsplit
class: with-icsc
size: A1
math: katex
paginate: false
title: 'QSplit: A Workflow-Oriented Hybrid Quantum–Classical Optimization Framework'
author: 'Mario Bifulco, Francesco Medina, Doriana Medić, Luca Roversi, Marco Aldinucci'
---

<div class="masthead">
<div class="brand">

![University of Turin](img/unito-logo.svg)

</div>
<div>

# <span class="project">QSplit:</span> A Workflow-Oriented Hybrid<br>Quantum-Classical Optimization Framework

<p class="authors"><strong>Mario Bifulco</strong> - Supervisors: Luca Roversi and Doriana Medić</p>
<p class="affiliation">University of Turin - Department of Computer Science</p>

</div>
<img class="icsc-logo" src="img/icsc.svg" alt="ICSC - Centro Nazionale di Ricerca in High Performance Computing, Big Data e Quantum Computing">
</div>

<div class="lead">

**Research focus**
How can hybrid quantum-classical workflows tackle optimization problems beyond QPU capacity while balancing solution quality and computational cost? QSplit investigates decomposition, compact encodings, and HPC-QPU integration

</div>

<div class="columns">
<div class="column">
<div class="block">

## <span class="num">01</span> Motivation

<div class="item">

### Quantum as an accelerator

Quantum computing is a candidate accelerator within HPC optimization workflows

</div>
<div class="item">

### Problems outgrow QPUs

Large optimization instances exceed the capacity of current noisy QPUs

</div>
<div class="item">

### Workflow portability

Different quantum backends require portable orchestration of heterogeneous resources

</div>
</div>
<div class="block">

## <span class="num">02</span> Objectives

- **Algorithmic objective**: Preserve solution quality when splitting large QUBOs into QPU-sized tasks
- **Systems objective**: Reduce variational training and data-transfer costs in portable HPC-quantum workflows

</div>
<div class="block">

## <span class="num">03</span> Research questions

- **RQ1 - Decomposition**: How can QUBO structure guide splitting and aggregation to preserve global solution quality?
- **RQ2 - Quantum cost**: Can compact encodings and reduced variational training lower resource use while preserving quality?
- **RQ3 - Integration**: How can heterogeneous solvers be integrated into portable HPC workflows with low overhead?

</div>
<div class="block">

## <span class="num">04</span> Problem & data

**Quadratic Unconstrained Binary Optimization (QUBO)**

<div class="formula">

$$\min_{x\in\{0,1\}^{n}} x^{\mathsf T}Qx \footnotesize\qquad Q\in\mathbb{R}^{n\times n}$$

</div>

QSplit accepts problems formulated as QUBOs. **Max-Cut** is the current test case; generalization depends on **instance structure**, including coefficient sparsity, distribution, and magnitude

![sparse-dense](img/sparse_dense.svg)

</div>
</div>
<div class="column middle">
<div class="block">

## <span class="num">05</span> Methodology

### A modular split-solve-aggregate pipeline

QSplit organizes splitting, solving and aggregation into **workflows** that link tasks through data dependencies, enabling reuse of steps and interchangeable solver backends.

<div class="streamflow-intro">
<a class="streamflow-brand" href="https://streamflow.di.unito.it/about-s/"><img src="img/streamflow-logo-full.png" alt="StreamFlow - Towards Cloud-HPC Continuum"></a>
<p>For <strong>RQ3</strong>, QSplit uses <strong>StreamFlow</strong> to execute workflows on heterogeneous resources and manage data transfers across hybrid infrastructures.</p>
</div>

<div class="workflow">

![Split-solve-aggregate workflow: input QUBO, split into subproblems (B), parallel CPU, GPU and QPU solvers (A), aggregate a global solution (B), and one-shot output (C). Ellipses indicate additional solvers.](img/workflow.svg)

</div>

<div class="method">

### <span class="letter">A</span> Quantum solvers

To address **RQ2**:

- **Fewer variational cycles**: Study QAOA parameterizations with fewer classical-quantum optimization loops
- **HPC training + QC optimization**: Train QAOA parameters on HPC resources, then use quantum resources for optimization
- **Compact quantum encoding**: Pauli Correlation Encoding (PCE) represents logical QUBO variables through correlations over fewer qubits

<div class="pce-placeholder">
<p>

![PCE](img/pce.svg)

</p>
</div>
</div>
<div class="method">

### <span class="letter">B</span> Structure-aware pipeline

To address **RQ1**, study splitting methods that preserve variable interactions within subproblems and limit information loss during aggregation

</div>
<div class="method">

### <span class="letter">C</span> One-shot approach

A single pass provides a baseline to study solution quality, resource use, and refinement

</div>
</div>
</div>
<div class="column">
<div class="block">

## <span class="num">06</span> Experimental platform

![QSplit deployments: IBM QAOA and D-Wave simulated annealing on CPUs, and CUDA-Q with GPU acceleration, on the HPC4AI cluster at UniTo; real QPUs: IQM Garnet and Quantinuum H2.](img/deployment.png)

</div>
<div class="block future">

## <span class="num">07</span> Current results

<div class="metrics">
<div class="metric-row">
<div class="metric">50x<span>Problem size vs QPU</span></div>
<div class="metric">- 99%<span>Variational loops</span></div>
</div>
<p>QSplit tackles problems larger than the QPU with reduced variational training and little loss of solution quality</p>
</div>

<p class="result-note">Initial evidence for <strong>RQ1-RQ2</strong> on Max-Cut; generalization to other QUBOs and integration costs (<strong>RQ3</strong>) remain to be evaluated</p>

<div class="comparison-placeholder">
<p>

![Quantum VS Classic](img/qvsc.svg)

</p>
</div>
</div>
<div class="block future">

## <span class="num">08</span> PhD roadmap

<div class="item">

### RQ1 - Refinement process

Develop optional post-aggregation refinement and assess the quality-resource trade-off

</div>
<div class="item">

### RQ2-RQ3 - Resource cost

Broaden benchmarks across QUBO structures and backends; measure qubit use, variational loops, runtime, and transfer costs

</div>
<div class="item">

### Beyond QUBO

Explore constraint-aware mixers (QOLC) and integer formulations (QUIO)

</div>
</div>
</div>
</div>
