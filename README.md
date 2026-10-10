# Does algebraic structure make lattice cryptography easier to break?

Public-key cryptography lets strangers establish a secret over a public channel. Its security depends on mathematical problems being expensive to solve. Efficient constructions often give those problems extra structure, making keys smaller and arithmetic faster. Does that same structure give an attacker a shortcut?

Matthew Green's [concern that we might lose public-key cryptography](https://x.com/matthew_d_green/status/2107992246360649879) motivates asking what evidence would change our confidence. This agenda starts with one tractable part: **when, and by how much, does ring or module structure reduce the cost of recovering a secret from noisy linear equations?** The first target is the problem underlying [ML-KEM](https://csrc.nist.gov/pubs/fips/203/final), a standard for establishing shared keys. An answer here would address one family of assumptions; it would not settle the future of all public-key cryptography.

## The comparison

In Learning with Errors (LWE), the attacker sees a matrix and a noisy product:

$$
b = As + e \pmod q.
$$

The task is to recover the hidden vector $s$. The matrix $A$ is public, $q$ is the modulus, and $e$ is a small random error. Dimensions, available equations, and the distributions of both secret and error all affect the difficulty.

Ordinary LWE samples the matrix entries independently. Module-LWE instead uses a matrix of polynomials; expanding polynomial multiplication produces a larger matrix with related entries. We can compare these two distributions at the same scalar dimensions, modulus, and coefficient distributions. Their different matrix structure is the variable under study. Related equations obtained by rotating a polynomial equation are not fresh independent samples.

Start with small, explicitly defined instances that existing algorithms can solve. Vary polynomial degree and module rank while holding total dimension fixed. Include a general-purpose lattice attack on both distributions, then test whether an algorithm that uses polynomial structure gains an advantage. Small instances make ideas cheap to check; a separate argument is needed to connect any improvement to cryptographic sizes.

## Questions worth resolving

1. **Is there a measurable cost to adding structure?** At matched parameters and resource budgets, do ring or module instances differ from ordinary LWE in recovery rate, time, or memory? Establish a reproducible baseline before searching for improvements.
2. **Which structure could explain a gap?** Can polynomial factorization modulo the modulus, ring symmetries, or maps to smaller rings help recover the secret? For a proposed transformation, derive what happens to the secret, error, and dependencies between equations. A smaller equation is useful only if the resulting problem is easier.
3. **Does an improvement survive realistic secrets?** Test whether an advantage persists for independently sampled small coefficients, or relies on unusually few nonzero coefficients, extra samples, or a special modulus. Record the exact boundary where it disappears. [Existing LWE benchmarks](https://arxiv.org/abs/2408.00882) provide useful attacks and examples of why secret distributions matter.
4. **What would change a concrete security estimate?** Compare measurements with a pinned version and explicit cost model of the [lattice estimator](https://github.com/malb/lattice-estimator). Identify the heuristic responsible for a mismatch. Separate a faster implementation, an algorithmic improvement, and evidence for different scaling; state which step towards ML-KEM parameters remains untested.

AI-assisted work is welcome at each step: proposing a transformation, finding a counterexample, tuning an attack, or proving why a tempting shortcut fails. Evaluate the resulting method against a tuned baseline on fresh instances, and report the compute spent discovering it separately from the cost of running it.

## Start here

Start with [Does module structure make matched small LWE instances easier to solve?](https://github.com/public-observatory/cryptographic-hardness/issues/1). The issue specifies the distributions, a pilot experiment, and the evidence needed for an answer. The first useful contribution can be a checked instance generator and baseline, without a new attack.

**Current state:** this repository states a research plan. It contains no experimental evidence of a structure advantage or a break of ML-KEM. As claims arrive, maintainers will summarize the best supported answer here, link disagreements and failed approaches, and identify the next unresolved question.

## What counts as progress

A proof must state its instance distribution and hypotheses. An experimental claim must include code, pinned dependencies, a reproduction command, hardware and resource limits, and per-instance results including timeouts and failures. Publish the generator and seeds for reproduction, but keep planted secrets and generation seeds unavailable to the solver during evaluation. Use separate tuning and evaluation instances. Report success rates with uncertainty; a timeout is a bounded observation, not evidence of hardness.

A failed idea is useful when it states what was tried, at what cost, and what the result rules out. A counterexample to a proposed reduction, or an explanation of why projected noise defeats an attack, can be as valuable as a speedup. Claims about deployed parameters must explain every change from the tested distribution and every extrapolation.

This is an open agenda: anyone may propose a subquestion or submit a claim, whether the work was done by a person, an agent, or both. Claims name the questions they address and link their code, data, or proofs. State provenance, including model and tools where applicable, and link a Palomar submission if available. Maintainers mark a claim reproduced only after someone other than its author checks it; questions close with a linked answer and its limits. Notes and longer arguments belong in [writeups/](writeups/). See the [contribution guide](https://public-observatory.github.io/docs.html) for the shared workflow.

## Background

- Regev, [On Lattices, Learning with Errors, Random Linear Codes, and Cryptography](https://arxiv.org/abs/2401.03703): the foundational reduction and its hypotheses.
- De Boer and van Woerden, [Lattice-based Cryptography: A survey on the security of the lattice-based NIST finalists](https://eprint.iacr.org/2025/304): attack families and the assumptions behind their analysis.
- NIST, [FIPS 203](https://csrc.nist.gov/pubs/fips/203/final): the target construction and exact ML-KEM parameters. Reduced experimental instances should be described as such.
