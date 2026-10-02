# Percolation on the Bethe lattice

An interactive, single-file web demo of site percolation on the Bethe lattice (Cayley tree), where every site has z neighbors and there are no loops, so the problem can be solved exactly. It is based on lecture notes by Sang Hoon Lee, which follow Section 1.3 of K. Christensen and N. R. Moloney, *Complexity and Criticality* (2005). It is a companion to the lattice and network percolation demos.

Everything runs in the browser. There is no build step, no server and no dependencies beyond an optional web font.

## Running it

Open `index.html` in any modern browser (Chrome, Edge, Firefox or Safari).

To publish it with GitHub Pages, push this repository, then go to **Settings → Pages**, choose **Deploy from a branch**, and select the branch and the root folder. The page will be served at `https://<user>.github.io/<repository>/`.

## What the page contains

One coordination number z (2, 3, 4 or 5, where z = 2 is the 1D chain) drives the whole page.

**Live Cayley tree.** A finite tree drawn in generations around the center site, with dotted circles for the chemical distance ℓ. A slider, a scan button and "Jump to p<sub>c</sub>" set the occupation probability p, and every site keeps its own random number, so raising p only adds sites. A coloring switch shows only the largest cluster (the default), every cluster in its own color (largest in blue), or only the center's cluster, with a share bar for the highlighted cluster. Readouts show the largest cluster, the number of clusters, the size of the center's cluster, the furthest generation it reaches, whether it touches the boundary, the expected size χ(p), and the share of boundary sites in the finite tree. A chart compares the center cluster's sites in each generation with the expected N(ℓ) = z(z − 1)<sup>ℓ−1</sup>p<sup>ℓ</sup>.

**The threshold and the order parameter.**

- the argument that a non-retracing walk needs p(z − 1) ≥ 1, so p<sub>c</sub> = 1/(z − 1), which is not universal
- the self-consistency equation Q<sub>∞</sub> = 1 − p + p Q<sub>∞</sub><sup>z−1</sup> and P<sub>∞</sub>(p) = p[1 − Q<sub>∞</sub><sup>z</sup>], solved exactly for every z
- the tangent 2z/(z − 2) · (p − p<sub>c</sub>) and the log–log slope β = 1, compared with simulation

**Average cluster size.** The recursion B = p[1 + (z − 1)B] gives χ(p) = (1 + p)/(1 − (z − 1)p) = p<sub>c</sub>(1 + p)/(p<sub>c</sub> − p), so γ = 1. Simulated values are also shown above p<sub>c</sub>, for finite clusters.

**Cluster numbers.**

- the perimeter t = 2 + s(z − 2) of every s-cluster
- the exact cluster numbers n(s, p) = g(s, t)(1 − p)<sup>t</sup>p<sup>s</sup> with the Fisher–Essam degeneracy g = z[(z − 1)s]! / (s! [(z − 2)s + 2]!)
- the characteristic size s<sub>ξ</sub> ∝ |p − p<sub>c</sub>|<sup>−2</sup> (σ = 1/2), and n(s, p<sub>c</sub>) ∝ s<sup>−5/2</sup> (τ = 5/2), compared with the simulated cluster sizes at p<sub>c</sub>

**Correlation function and the sum rule.** g(ℓ) = p<sup>ℓ</sup> along the unique path, N(ℓ) = [z/(z − 1)]e<sup>−ℓ/ℓ<sub>ξ</sub></sup> with ℓ<sub>ξ</sub> = −1/ln(p/p<sub>c</sub>), and the sum rule 1 + Σ N(ℓ) = χ(p), checked exactly and by simulation.

**Exponents and the coordination number.** A table of p<sub>c</sub> and the amplitudes for z = 2 to 5 with identical exponents. A second table compares the exact mean-field exponents with the simulation and lists the relations β = (τ − 2)/σ, γ = (3 − τ)/σ, σ = 1/(νD), and hyperscaling, which gives the upper critical dimension d = 6 from D = 4 and ν = 1/2.

## Methods

| Topic | Approach |
| --- | --- |
| Exact curves | Q<sub>∞</sub> by bisection on the nontrivial root; closed forms for χ, n(s, p), s<sub>ξ</sub> and N(ℓ); log-gamma for large factorials |
| Simulation | The center's cluster on an infinite tree grows as a branching process. The center is occupied, it has z children, every later site has z − 1, and each child is occupied with probability p. Only the number of sites per generation is tracked, drawn from binomial distributions. |
| "Infinite" clusters | A cluster still growing after 4 000 generations, or with more than 200 000 sites in one generation, counts as infinite |
| Live tree | A finite Cayley tree with angles assigned in proportion to the number of leaves below each branch |

Simulated exponents come close to the exact values; "Add more samples" reduces the noise.

## Files

```
index.html   the complete demo (HTML, CSS and JavaScript in one file)
README.md    this file
```

## References

**Key reference.** K. Christensen and N. R. Moloney, *Complexity and Criticality*, Imperial College Press, London (2005). Section 1.3 covers percolation on the Bethe lattice, and Exercise 1.7 the order parameter for general z.

1. H. A. Bethe, "Statistical theory of superlattices," *Proc. R. Soc. Lond. A* **150**, 552 (1935).
2. M. E. Fisher and J. W. Essam, "Some cluster size and percolation problems," *J. Math. Phys.* **2**, 609 (1961).
3. D. Stauffer and A. Aharony, *Introduction to Percolation Theory*, 2nd ed., Taylor & Francis, London (1994).
4. T. E. Harris, *The Theory of Branching Processes*, Springer, Berlin (1963).

## Credits

Lecture notes: Sang Hoon Lee.

Created by Claude Opus 5.5.
