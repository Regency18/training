
# nanoMoE

Cloned nanoMoE to plot memory consumption of MoE while training.

## install

```
pip install torch numpy transformers datasets tiktoken wandb tqdm
```

Dependencies:

- [pytorch](https://pytorch.org) <3
- [numpy](https://numpy.org/install/) <3
-  `transformers` for huggingface transformers <3 (to load GPT-2 checkpoints)
-  `datasets` for huggingface datasets <3 (if you want to download + preprocess OpenWebText)
-  `tiktoken` for OpenAI's fast BPE code <3
-  `wandb` for optional logging <3
-  `tqdm` for progress bars <3

#### Run Pretraining

To run:

```sh
git clone https://github.com/wolfecameron/nanoMoE.git
cd nanoMoE
python data/shakespeare_char/prepare.py

python train.py config/train_shakespeare_char.py
```
The link for the pytorch memory visualizer : [memory_viz](https://pytorch.org/memory_viz) <3

Here's my graphs that I got: 
[epoch 1]()
[epoch 50]()
[epoch 99]()
[full 100 epochs]()
