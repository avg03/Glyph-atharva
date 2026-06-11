# Week 2: Data Engineering, Stroke Visualiser and Baseline VAE

Set up your data pipeline, build the stroke engine, and implement a baseline VAE that can compress and reconstruct a doodle.

* Topics: Quick Draw dataset, stroke-3 format, delta coordinates, normalisation, PyTorch Dataset, Matplotlib animation, LSTM encoder, VAE, KL divergence, latent space

---

## Welcome to Week 2

This week covers more ground than usual because we are on a tighter schedule, so pace yourself and start early.

The first half is about data -- loading, cleaning, and visualising the Quick Draw dataset. The second half is where things get interesting: you will implement a baseline VAE that compresses a full sketch into a small latent vector `z` and reconstructs it back. By the end of this week you will have a model that can actually draw.

This week has two checkpoints:

* **Checkpoint 1 -- The Stroke Engine:** a working stroke-by-stroke sketch animator
* **Checkpoint 2 -- Latent Compression:** a baseline VAE that compresses and redraws a simple doodle

This week has 5 notebooks.

* Quick Draw data engineering (Fill the TODOs in `quickdraw_data.ipynb`)
* Stroke visualiser (Fill the TODOs in `stroke_visualiser.ipynb`)
* LSTM encoder (Fill the TODOs in `lstm_encoder.ipynb`)
* VAE decoder and training (Fill the TODOs in `vae.ipynb`)
* Assignment (Fill the TODOs in `assignment/assignment.ipynb`)

---

## Background Reading

### The Quick, Draw! dataset

Start here before touching any code. Open the link below, pick 5 different categories, and watch the strokes animate. Pay attention to: what order strokes are drawn in, where the pen lifts, and how different people draw the same object differently.

[quickdraw.withgoogle.com/data](https://quickdraw.withgoogle.com/data)

---

### The stroke-3 format -- SketchRNN paper Sections 1 and 3.1

Read Section 1 (Introduction) and Section 3.1 carefully. Section 3.1 explains exactly how a drawing becomes a sequence of `(dx, dy, pen_lifted)` numbers -- this is the data format the entire project runs on. Section 1 motivates why this representation is useful.

[arxiv.org/abs/1704.03477](https://arxiv.org/abs/1704.03477)

---

### Quick Draw GitHub repository

The official repo from Google. Has the `.ndjson` format documented clearly, dataset statistics, and a list of all 345 categories. Skim the README.

[github.com/googlecreativelab/quickdraw-dataset](https://github.com/googlecreativelab/quickdraw-dataset)

---

### Matplotlib FuncAnimation

You will use `FuncAnimation` to animate the stroke-by-stroke drawing. This short tutorial covers exactly what you need.

[Matplotlib animation tutorial](https://matplotlib.org/stable/users/explain/animations/animations.html)

---

### PyTorch Dataset and DataLoader

You will wrap the data in a `Dataset` class. This tutorial explains how Dataset and DataLoader work together, including how to handle variable-length sequences with padding.

[PyTorch data loading tutorial](https://pytorch.org/tutorials/beginner/data_loading_tutorial.html)

---

### Understanding VAEs

This is the core architecture of the project. Read this fully before starting the VAE notebooks. It explains what the encoder and decoder do, what the latent space `z` represents, and why the KL divergence term exists in the loss.

[Understanding Variational Autoencoders -- Towards Data Science](https://towardsdatascience.com/understanding-variational-autoencoders-vaes-f70510919f73)

---

### LSTMs for sequence modeling

The encoder and decoder both use LSTMs to process stroke sequences. Read this short explainer -- it covers hidden states, cell states, and why LSTMs handle sequences better than plain RNNs.

[Understanding LSTMs -- Colah's blog](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)

---

### SketchRNN paper Section 3 (Model)

Now go back to the paper and read Section 3 fully. It describes the exact encoder-decoder architecture you will implement this week: a bidirectional LSTM encoder that produces `mu` and `sigma`, a reparameterisation trick, and an autoregressive LSTM decoder. You do not need to follow every equation -- focus on the architecture diagram and the loss function description.

[arxiv.org/abs/1704.03477](https://arxiv.org/abs/1704.03477)

---

## References

[Quick, Draw! dataset](https://quickdraw.withgoogle.com/data)
[Quick Draw GitHub repo](https://github.com/googlecreativelab/quickdraw-dataset)
[Ha and Eck -- SketchRNN paper](https://arxiv.org/abs/1704.03477)
[Understanding VAEs -- Towards Data Science](https://towardsdatascience.com/understanding-variational-autoencoders-vaes-f70510919f73)
[Understanding LSTMs -- Colah's blog](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)
[Matplotlib FuncAnimation docs](https://matplotlib.org/stable/api/_as_gen/matplotlib.animation.FuncAnimation.html)
[PyTorch Dataset and DataLoader tutorial](https://pytorch.org/tutorials/beginner/data_loading_tutorial.html)
[PyTorch nn.LSTM docs](https://pytorch.org/docs/stable/generated/torch.nn.LSTM.html)