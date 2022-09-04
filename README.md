# local-diffusion

local stable diffusion for the M1 mac.

this is an opinionated project setup based
on [this blog post](https://replicate.com/blog/run-stable-diffusion-on-m1-mac).

thanks to @bfirsh for getting stable-diffusion to work on the M1 GPU!

## setup

1. git clone this project with `--recursive-submodules`.
2. create a python 3.10 env (recommended: with anaconda) and `pip install -r requirements.txt`
3. download the weights from [hugging face](https://huggingface.co/CompVis/stable-diffusion-v-1-4-original), then link:
   `ln -s <path/to/sd-v1-4.ckpt> mac-diffusion/models/ldm/stable-diffusion-v1/model.ckpt`

## run

```commandline
python mac-diffusion/scripts/txt2img.py \
  --prompt "a red juicy apple floating in outer space, like a planet" \
  --n_samples 1 --n_iter 1 --plms --precision full
```

_note: if you hit a bfloat16 error, add `--precision full`
([thanks](https://news.ycombinator.com/item?id=32684001) @whyboris)._

