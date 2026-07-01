# Glyph: Hierarchical Auto-Encoder 

Welcome! This repository contains all the resources and assignments to guide you through your journey.

---

## Week 0: Introduction and Python Basics

Set up your coding environment and get familiar with Python, NumPy and Matplotlib.

- **Topics**: Python, Jupyter Notebook, NumPy, Matplotlib, GitHub

---

## Week 1: PyTorch Foundations & Project Context

Set up PyTorch and master its core concepts -- tensors, autograd, and training loops -- while getting your first look at how Scribe thinks about sketches.

- **Topics**: PyTorch, Tensors, Autograd, nn.Module, Optimizers, MLP, Sketch sequences

---

## Week 2: Data Engineering, Stroke Visualiser and Baseline VAE

Set up your data pipeline, build the stroke engine, and implement a baseline VAE that can compress and reconstruct a doodle.

- **Topics**: Quick Draw dataset, stroke-3 format, delta coordinates, normalisation, PyTorch Dataset, Matplotlib animation, LSTM encoder, VAE, KL divergence, latent space

---

## Week 3: Hierarchical Architecture and Probabilistic Outputs

Upgrade the data format, build the Conductor-Worker hierarchy, and add a Mixture Density Network so the model can generate diverse completions.

- **Topics**: Stroke-5 format, variable-length batching, Conductor RNN, Worker RNN, Mixture Density Networks, temperature sampling, NLL loss