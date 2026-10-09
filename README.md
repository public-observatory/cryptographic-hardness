# Structure and hardness in cryptography

**When does the structure that makes a cryptographic construction efficient also make its underlying computational problem easier?**

Many cryptographic constructions rely on the difficulty of solving equations with partial or noisy information. A central example is Learning with Errors (LWE): recover a secret vector $s$ from

$$
b = As + e \pmod q,
$$

where $A$ is a public matrix with $m$ rows and $n$ columns over the integers modulo $q$, and $e$ is a small random error vector. The difficulty depends on the dimensions, modulus, secret and error distributions, and any algebraic structure imposed on $A$.

Lattice cryptography offers reductions connecting certain average-case problems to worst-case lattice problems. These provide evidence for hardness under specified assumptions, but do not by themselves determine the cost of solving a particular parameter set. Understanding that cost, and the role of structure in it, is the core problem.

OpenAI's [2026 collection of AI-generated mathematical results](https://github.com/openai/math), at varying stages of verification, motivates asking whether similar methods can advance the algorithms studied here. Progress on other mathematical problems does not itself establish a cryptographic weakness: the relevant question is whether a new algorithm lowers the cost of solving the instance distributions used in cryptography.

Three directions seem promising:

- **Structure and algorithms.** Which features of ring and module variants of LWE can algorithms exploit beyond generic lattice reduction? How do these interact with sparse secrets and the error distribution?
- **Concrete complexity.** How does the best known computational cost vary with the parameters? Identify where estimates depend on untested heuristics, and distinguish improvements in constants from changes in asymptotic scaling.
- **Assumptions and constructions.** Which hardness assumptions are needed for signatures, proofs, and public-key encryption? Study when lattice assumptions can be replaced by hash assumptions, and where reductions or barriers limit such replacements.

A concrete starting point is to compare unstructured and module-LWE instances at matched total dimension, modulus, sample count, and secret and error distributions. Measure the time, memory, and success probability of tuned classical algorithms and AI-assisted variants. Explain observed differences mathematically where possible, and state what remains uncertain when extrapolating to larger instances.

Contributors are welcome to take ownership of a question through an issue and develop proofs, reproducible experiments, or alternative approaches.

## References

- Regev (2009; corrected version 2024), [On Lattices, Learning with Errors, Random Linear Codes, and Cryptography](https://arxiv.org/abs/2401.03703).
- De Boer and van Woerden (2025), [Lattice-based Cryptography: A survey on the security of the lattice-based NIST finalists](https://eprint.iacr.org/2025/304).
- Wenger et al. (2025), [Benchmarking Attacks on Learning with Errors](https://arxiv.org/abs/2408.00882); Karenin et al. (2025), [Cool + Cruel = Dual, and New Benchmarks for Sparse LWE](https://eprint.iacr.org/2025/1002).
- Impagliazzo and Rudich (1989), [Limits on the Provable Consequences of One-Way Permutations](https://doi.org/10.1145/73007.73012).
- NIST (2024), [Stateless Hash-Based Digital Signature Standard](https://csrc.nist.gov/pubs/fips/205/final); Ben-Sasson et al. (2018), [Scalable, transparent, and post-quantum secure computational integrity](https://eprint.iacr.org/2018/046).
- Fluri et al. (2026), [CryptanalysisBench: Can LLMs do Cryptanalysis?](https://arxiv.org/abs/2607.18538).
