# Structure and hardness in cryptography

**When does the structure that makes a cryptographic construction efficient also make its underlying computational problem easier?**

Lattice cryptography connects security to problems such as Learning with Errors (LWE): recovering a secret from noisy linear equations. Its [hardness reductions](https://arxiv.org/abs/2401.03703) leave open important questions about concrete computational costs. OpenAI's [recent mathematical results](https://github.com/openai/math) motivate revisiting these questions with AI-assisted methods, without themselves establishing cryptographic weaknesses.

Three possible directions:

- **Algebraic structure.** When can algorithms exploit ring or module structure beyond generic lattice reduction?
- **Parameter dependence.** How do dimension, noise, and secret distributions affect computational cost, and where are current estimates least understood?
- **Necessary assumptions.** When can signatures and proofs use hash assumptions in place of lattice assumptions, and what obstructs analogous replacements for public-key encryption?

A starting point is to compare unstructured and module-LWE at matched dimensions, modulus, sample count, and secret and error distributions. Build on [existing benchmarks](https://arxiv.org/abs/2408.00882) and [revised classical baselines](https://eprint.iacr.org/2025/1002), seeking both reproducible measurements and mathematical explanations.

These are starting questions. Contributors are welcome to take one forward or propose another through an issue.
