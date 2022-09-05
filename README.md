# local-diffusion

local stable diffusion for the M1 mac.

this is an opinionated project setup based
on [this blog post](https://replicate.com/blog/run-stable-diffusion-on-m1-mac).

thanks to the folks in [CompVis/stable-diffusion#25](https://github.com/CompVis/stable-diffusion/issues/25) for getting this working on the M1!

## setup

1. git clone this project with `--recursive-submodules`.
2. `conda env create --file mac-diffusion/environment-mac.yaml --name ldm-mac && conda activate ldm-mac`
3. download the weights from [hugging face](https://huggingface.co/CompVis/stable-diffusion-v-1-4-original), then link:
   `ln -s <path/to/sd-v1-4.ckpt> mac-diffusion/models/ldm/stable-diffusion-v1/model.ckpt`
4. `export PYTORCH_ENABLE_MPS_FALLBACK=1`

## run

```commandline
python mac-diffusion/scripts/txt2img.py \
  --n_samples 1 --n_iter 1 --plms --precision full \
  --prompt "a red juicy apple floating in outer space, like a planet" 
```

_note: if you hit a bfloat16 error, add `--precision full`
([thanks](https://news.ycombinator.com/item?id=32684001) @whyboris)._

