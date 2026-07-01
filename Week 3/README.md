# Week 3: Hierarchical Architecture and Probabilistic Outputs

Upgrade the data format, build the Conductor-Worker hierarchy, and add a Mixture Density Network so the model can generate diverse completions instead of a single deterministic output.

* Topics: Stroke-5 format, variable-length batching, Conductor RNN, Worker RNN, sub-goal vectors, Mixture Density Networks, temperature sampling, NLL loss

---

## Welcome to Week 3

This week is the core of Scribe. We start by wrapping up a couple of things from last week -- upgrading to the stroke-5 format and fixing our batching properly. Then we build the full hierarchical model: a Conductor that plans the drawing at a high level, a Worker that executes it stroke by stroke, and an MDN head that makes the outputs probabilistic so the model can generate many different completions from the same starting sketch.

This week has two checkpoints and two separate assignments. Do not skip Assignment 1 and jump straight to Assignment 2 -- they build on each other.

* **Checkpoint 3 -- Hierarchical Flow:** the Conductor correctly guides the Worker
* **Checkpoint 4 -- Creative Diversity:** the model generates multiple unique completions for the same starting line

This week has 5 notebooks.

* Stroke-5 format and proper batching (Fill the TODOs in `stroke5_format.ipynb`)
* Conductor-Worker architecture (Fill the TODOs in `conductor_worker.ipynb`)
* Mixture Density Networks (Fill the TODOs in `mdn.ipynb`)
* Assignment 1 (Fill the TODOs in `assignment1/assignment1.ipynb`)
* Assignment 2 (Fill the TODOs in `assignment2/assignment2.ipynb`)

---

## Background Reading

### Stroke-5 format -- SketchRNN paper Section 3.1

Re-read Section 3.1 of the SketchRNN paper with fresh eyes. This time focus on the stroke-5 representation and how the three pen state flags `(p1, p2, p3)` differ from the single `pen_lifted` flag we used last week. The end-of-sequence token is also introduced here -- make sure you understand what it signals.

[arxiv.org/abs/1704.03477](https://arxiv.org/abs/1704.03477)

---

### Hierarchical Latent Vector Model -- Roberts et al., 2018

This is the paper behind the Conductor-Worker architecture we build this week. Read Section 1 and Section 3. The key idea: a high-level Conductor network plans the sequence in coarse segments, and a low-level Worker executes fine-grained steps within each segment. The paper applies this to music but the architecture maps directly to sketches.

[arxiv.org/abs/1803.05428](https://arxiv.org/abs/1803.05428)

---

### Mixture Density Networks -- Bishop, 1994

The original MDN paper. It is short and very readable. Read Sections 1 and 2. The key idea: instead of predicting a single output, the network predicts the parameters of a mixture of Gaussians and we sample from it. This is what gives Scribe its ability to generate diverse completions.

[Bishop, 1994 -- Mixture Density Networks](https://publications.aston.ac.uk/id/eprint/373/1/NCRG_94_004.pdf)

---

### MDN intuitive explainer

If the original paper feels heavy, read this blog post first. It covers the same ideas with code examples and good visualisations.

[Mixture Density Networks -- David Ha](http://blog.otoro.net/2015/11/24/mixture-density-networks-with-tensorflow/)

---

### pack_padded_sequence -- PyTorch docs

We use this to handle variable-length sequences efficiently in the LSTM. Read the docstring and the example carefully -- this is one of the trickier PyTorch utilities and it trips most people up the first time.

[PyTorch -- pack_padded_sequence](https://pytorch.org/docs/stable/generated/torch.nn.utils.rnn.pack_padded_sequence.html)

---

## References

[Ha and Eck -- SketchRNN paper](https://arxiv.org/abs/1704.03477)
[Roberts et al. -- Hierarchical Latent Vector Model](https://arxiv.org/abs/1803.05428)
[Bishop -- Mixture Density Networks (1994)](https://publications.aston.ac.uk/id/eprint/373/1/NCRG_94_004.pdf)
[David Ha -- MDN blog post](http://blog.otoro.net/2015/11/24/mixture-density-networks-with-tensorflow/)
[PyTorch -- pack_padded_sequence](https://pytorch.org/docs/stable/generated/torch.nn.utils.rnn.pack_padded_sequence.html)
[PyTorch -- nn.LSTM](https://pytorch.org/docs/stable/generated/torch.nn.LSTM.html)
[PyTorch Dataset and DataLoader tutorial](https://pytorch.org/tutorials/beginner/data_loading_tutorial.html)