# **Background Readings**

1. What are we building and why?
Start here. Watch this 3-minute demo by the authors of SketchRNN.
[Sketch-RNN Demo](https://magenta.tensorflow.org/sketch-rnn-demo)

2. Paper — A Neural Representation of Sketch Drawings (Ha & Eck, 2017)
This is the core paper behind everything we build in Glyph. You are not expected to understand every equation, but you should read and understand:
- Abstract — what problem is being solved
- Section 1 (Introduction) — why treating a sketch as a sequence is a good idea
- Section 3.1 — how a sketch is represented as (Δx, Δy, p1, p2, p3) tuples
This paper has been provided in the current directory.

3. What is a VAE?
[Understanding Variational Autoencoders](https://towardsdatascience.com/understanding-variational-autoencoders-vaes-f70510919f73)
This website provides a good answer to the question posed.

4. Architecture - Hierarchical VAEs for Music (Roberts et al., 2018)
This is where the Conductor-Worker idea comes from. The paper applies it to music but the architecture is identical to what we build in Week 4. Read Section 1 and Section 3 only.
This paper has been provided in the current directory.
