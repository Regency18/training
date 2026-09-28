
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

## quick start

The [current configuration file](config/train_nano_moe.py) is created for a 2x3090 GPU setup on a single node.
The full pretraining script trains nanoMoE, a 6-layer MoE-based decoder-only transformer with 8 experts and 2 active experts, on ~25B tokens of the OpenWebText dataset in ~5 days.
If you have access to more GPUs, you can scale down `gradient_accumulation_steps` and scale up the `batch_size` accordingly.
You can also scale up `max_iters` to increase the number of tokens on which nanoMoE is trained.

#### Run Pretraining

Then we're ready to kick off training. To reproduce nanoMoE, you'll want to run:

```sh
git clone https://github.com/wolfecameron/nanoMoE.git
cd nanoMoE
python data/shakespeare_char/prepare.py
python train.py config/train_shakespeare_char.py
```


## troubleshooting

Note that by default this repo uses PyTorch 2.0 (i.e. `torch.compile`). This is fairly new and experimental, and not yet available on all platforms (e.g. Windows). If you're running into related error messages try to disable this by adding `--compile=False` flag. This will slow down the code but at least it will run.

For some context on this repository, GPT, and language modeling it might be helpful to watch Andrej's [Zero To Hero series](https://karpathy.ai/zero-to-hero.html). Specifically, the [GPT video](https://www.youtube.com/watch?v=kCc8FmEb1nY) is popular if you have some prior language modeling context. For context specifically on MoEs, check out the related [blog post](https://cameronrwolfe.substack.com/nano-moe) for this nanoMoE repository. 

For more questions/discussions feel free to stop by **#nanoGPT** on Discord:

[![](https://dcbadge.vercel.app/api/server/3zy8kqD9Cp?compact=true&style=flat)](https://discord.gg/3zy8kqD9Cp)

## acknowledgements

Thank you to Andrej Karpathy to providing an awesome [starting point](https://github.com/karpathy/nanoGPT) for the nanoMoE implementation!
