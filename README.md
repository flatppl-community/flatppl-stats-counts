# flatppl-stats-counts

[Function reference](docs/reference.md) · [Live example](https://live.flatppl.org/#model=https%3A%2F%2Fraw.githubusercontent.com%2Fflatppl-community%2Fflatppl-stats-counts%2Fmain%2Fexamples%2Fplayground.flatppl&target=Pi_post)

For source mean $s\geq0$, ON background mean $b\geq0$, and OFF/ON exposure ratio $\rho>0$:

$$N\sim\mathrm{Poisson}(s+b),\qquad M\sim\mathrm{Poisson}(\rho b),\qquad N\perp M\mid(s,b,\rho).$$

Library **0.1** returns normalized laws on nonnegative integer counts, plus the conditional estimate $\widehat b(s)$, profile log likelihood $\ell(s,\widehat b(s))$, and exact marginal under an explicit $b\sim\mathrm{Gamma}(a,r)$ prior (shape/rate).

```flatppl
flatppl_compat = "0.1"
counts = load_module("main.flatppl")
observation = counts.onoff(3.0, 2.0, 5.0)
score = logdensityof(observation, record(on = 7, off = 12))
```

All inputs are scalar. Means are expected counts. The usual ON/OFF exposure parameter is $\alpha=1/\rho$. ON and OFF samples must be disjoint. Only the Gamma marginal supplies a background prior.

The [synthetic laboratory example](examples/lab.flatppl) exposes count densities, a background estimate, and a profile likelihood.

See the reference for definitions, domains, numerical limits, and validation commands.
