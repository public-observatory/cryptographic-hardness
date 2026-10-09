# Safeguarding cryptography under accelerated mathematical discovery

**How can cryptography remain secure if AI rapidly improves the algorithms used to attack it?**

Cryptography relies on mathematical problems remaining expensive to solve. OpenAI's recent [mathematical release](https://github.com/openai/math), with results at different stages of verification, gives fresh motivation to examine these assumptions. [Vitalik Buterin's concern](https://x.com/VitalikButerin/status/2107976296320106851) is that new mathematics could weaken even quantum-resistant schemes, especially lattice-based signatures and encryption.

There is a concrete precedent: an AI-assisted attack led to the withdrawal of [Hawk](https://hawk-sign.info/), a lattice-based signature candidate. This was a weakness of that construction, not a general break of lattices. The broader risk remains an open research question.

The aim is to turn this concern into evidence that helps safeguard cryptography. Three directions seem promising:

- **Lattice security margins.** Which algebraic structure or parameter choices allow unexpectedly efficient attacks? Study signatures, key establishment, and fully homomorphic encryption separately. When do larger parameters restore security, and when must the construction change?
- **Hash-based alternatives.** When can signatures and proofs rely on hashes instead of lattice or elliptic-curve assumptions? Compare their costs under explicit assumptions about improved attacks, and examine the security margins of the hashes themselves.
- **Resilient encryption.** Public-key encryption has no established general replacement based on hashes alone. Can combinations of lattice and code-based schemes preserve security when one assumption fails? How much can limiting the publication and retention of ciphertexts reduce exposure to future attacks?

A concrete starting point is to extend existing Learning with Errors benchmarks with AI-assisted algorithm discovery. Vary dimension, secret density, and algebraic structure; compare against tuned classical attacks; and report reproducible time and memory costs. Use the results to assess parameter margins, keeping extrapolations explicit.

Contributors are welcome to take ownership of any direction. Open an issue with a precise question, then share proofs, reproducible experiments, or informative failed approaches. Alternative starting points are welcome.

## References

- De Boer and van Woerden (2025), [Lattice-based Cryptography: A survey on the security of the lattice-based NIST finalists](https://eprint.iacr.org/2025/304).
- Wenger et al. (2025), [Benchmarking Attacks on Learning with Errors](https://arxiv.org/abs/2408.00882), and Karenin et al. (2025), [Cool + Cruel = Dual, and New Benchmarks for Sparse LWE](https://eprint.iacr.org/2025/1002), which revisits the classical baselines.
- NIST (2024), [Stateless Hash-Based Digital Signature Standard](https://csrc.nist.gov/pubs/fips/205/final); Ben-Sasson et al. (2018), [Scalable, transparent, and post-quantum secure computational integrity](https://eprint.iacr.org/2018/046).
- Giacon, Heuer, and Poettering (2018), [KEM Combiners](https://eprint.iacr.org/2018/024).
- Fluri et al. (2026), [CryptanalysisBench: Can LLMs do Cryptanalysis?](https://arxiv.org/abs/2607.18538).
