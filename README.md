# Minds Like Ours: curling listings

WebPPL code for Listings 1 and 2 in Brooke-Wilson, T., & Tenenbaum, J. B., *Minds Like Ours: Scaling Model Synthesis Architectures for AI*. The chapter presents these programs as pseudocode; the files here are the full models.

| File | Listing | What it does |
|---|---|---|
| `listing1.wppl` | Listing 1 | A spectator's model of a single curling throw. After seeing one stone stop at 42 m, 7.25 m past the center, it infers how hard the stone was thrown and how much friction the ice has, estimates where the stone would have stopped if it had been swept, and chooses how hard to throw the next stone. |
| `listing2.wppl` | Listing 2 | The repaired model. After three long stones from both teams (42, 45, and 44 m), it adds a variable for a reduction in the ice's friction and attributes the overshoots to faster ice rather than harder pushes. |

## Running the code

The easiest way is in a browser. Go to [webppl.org](https://webppl.org), paste the contents of either file into the editor, and press **run**. Listing 1 takes a few seconds; Listing 2 can take a minute or more, because rejection sampling must discard many simulated throws before it finds runs consistent with all three observations. Each listing prints its inferences along with plots of the inferred distributions.

To run the code locally instead, install [WebPPL](https://github.com/probmods/webppl) with `npm install -g webppl` and use `webppl listing1.wppl`. The plotting calls (`viz`) only work in the browser, so comment them out when running from the command line.

## Expected results

Inference uses rejection sampling with 1,000 samples, so results vary from run to run. The best value of K varies most, typically by about ±0.01–0.02, because the chance of stopping near the center changes slowly around its peak. Typical values:

| | Listing 1 | Listing 2 |
|---|---|---|
| First push, relative to usual | ≈ 1.08 | ≈ 0.99 |
| Usual friction of the ice (μ) | ≈ 0.0147 | ≈ 0.0150 |
| Distance if the first stone had been swept | ≈ 46.6 m | (not queried) |
| Friction now, as a fraction of usual | (not modeled) | ≈ 0.81 |
| Best push for the next stone, relative to usual (K) | ≈ 0.99 | ≈ 0.90 |

## Citation

If you use this code, please cite the chapter. To cite the code itself, use the citation on its Zenodo page or in `CITATION.cff`.
