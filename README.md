# COMP90073 Workshop Week 10: Iterative FGSM, Autodiff, and the Robust Generalisation Gap

An interactive workbook for the Week 10 tutorial, grounded in COMP90073 Lecture 16 (generating adversarial examples: linear geometry, norms, FGSM, PGD), Lecture 17 (computational graphs and automatic differentiation), Lecture 18 (black-box and transfer attacks) and the Week 10 tutorial answers.

Live site: [hesamasad.github.io/week-10-attacks-autodiff-robustness](https://hesamasad.github.io/week-10-attacks-autodiff-robustness/). Open [`index.html`](index.html) locally in a browser if you prefer. The only external requests are Google Fonts and KaTeX. A Light / Dark / Auto switch sits in the sidebar.

Each question starts with the prerequisites it needs, explained inline with a figure you can play with. A simpler warm-up exercise follows, with self-checking answer boxes, hints and a hidden solution. Then comes a live version of the question, then the official answer behind a reveal.

## Question-by-question sequence

| Question | Prerequisites (inline) | Interactive check |
|---|---|---|
| 1 · Iterative FGSM on \(f(\mathbf x) = 2x_1 - x_2 + 0.5\) | the linear boundary and its constant gradient; \(\ell_1/\ell_2/\ell_\infty\) balls and why \(\epsilon\,\mathrm{sign}(w)\) is the best \(\ell_\infty\) step; FGSM, iterative FGSM and the clip projection | draggable plane with shortest \(\ell_2\)/\(\ell_\infty\) paths; rotatable norm balls; step-by-step attack from \((1,3)\) with \(\epsilon\), \(\alpha\), step count, early stop and a table of iterates |
| 2 · Forward vs reverse autodiff for \(y = \cos(e^{x_1}) - \sin(x_1/x_2 + 2x_2)\) | Jacobians and the chain rule as a matrix product; the \(mnp\) cost of a product; the computational graph | graph at \((2,4)\) with animated values, forward tangents and reverse adjoints; animated matrix chain (16 vs 12 multiplications); input/output scaling bars; symbolic and numeric Jacobians; partition explorer for parts (b) and (c) |
| 3 · Generalisation gap under adversarial training | clean vs robust accuracy and gap; the min–max objective | a 2–32–32–2 network trained in the browser with standard or PGD adversarial training (robust gap roughly doubles at 30 points and shrinks with more data); boundary-tilting slider |

## Warm-up exercises

| Before | Warm-up | Source |
|---|---|---|
| Q1 | one FGSM step on \(f(\mathbf x) = x_1 + x_2 - 3\) from \((1,1)\); the minimal budget \(\epsilon^\star = 1/2\); one \(\ell_\infty\) projection | Lecture 16, slides 6–8 and 15 |
| Q2 | forward and backward pass through \(\sigma(wx+b)\) with BCE at \(x=2, w=0.5, b=0, y=1\); a finite-difference check; forward vs reverse counts for a one-input chain (8 vs 9) | Lecture 17, slide 24; Lecture 16, slide 34; Lecture 18, slide 5 |
| Q3 | clean vs robust accuracy of a threshold classifier on a number line (clean gap 0, robust gap 75 points) | written for this workbook |

## Notes for the tutorial

- The official answer to Q2 never evaluates the gradient at \((2,4)\): it is \([-6.4542,\ 1.1288]\) (checked against finite differences on the page).
- The official sheet writes \(h(\mathbf b) = [b_0 - b_1]\) (zero-indexed) and the last reverse factor as \(f_{\mathbf a}\); it means \(f_{\mathbf x}\).
- For the merged partition in (c), reverse mode costs 9 as stated; forward mode costs 8.
- In Q1, a step of 1 overshoots: the smallest \(\ell_\infty\) change that flips \((1,3)\) is \(1/6\), and the projection never activates.

Keys: `]` / `[` next and previous section, `P` present mode, `L` light/dark.
