---
title: Your content
---

**TODO: this page is yours.** Delete everything below and replace it with your work
from Lab 1, Exercise 3.

## Suggested structure

Exercise 3 has four parts, and each is a candidate chapter:

| Part | The question | A slider worth building |
|---|---|---|
| A | k-space → image | none — this is your artifact-free reference |
| B | mask the centre of k-space | fraction kept: 1.0 → tiny |
| C | downsample k-space | keep every *R*th line: 1 → severe |
| D | head rotation mid-scan | the angle, **and** when it happened |

## What makes a good interactive figure

Ask what the static version of the figure *couldn't* tell the reader.

Part D is the clearest case. In Lab 1 you fixed one rotation angle and one k-space line.
But the k-space line is the interesting parameter: motion before the first line just
rotates the image, motion after the last line does nothing at all, and the worst case is
the **centre of k-space**. A slider shows that in three seconds. A static figure can only
assert it.

That reasoning — *which parameter deserves a slider, and over what range* — is the part
being assessed. It's also the part an LLM can't do for you, because it depends on what
you're trying to explain.

## Show your working

Put your code in a dropdown, the way
[](./02-interactive-figures.md) does, so the page stays readable and the work stays
visible.

## Reflection

**TODO:** answer these in your own words.

1. Which artifact from Lab 1 is better explained interactively than statically, and why?
2. What question can your figure **not** answer? Your slider only chooses among the
   frames you precomputed — so what would you have had to compute to answer it?
