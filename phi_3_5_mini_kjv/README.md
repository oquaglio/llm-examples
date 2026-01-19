#

## About



## Setup

### Create Python Venv

Note: PyTorch only supports 3.12 as of December 29, 2025

```sh
uv python pin 3.12
uv venv
source .venv/bin/activate
```

### Install into venv

Install compatible PyTorch 2.5.1 stack (fast, matches cu121 driver support):

```sh
uv pip install torch==2.5.1 torchvision==0.20.1 torchaudio==2.5.1 --index-url https://download.pytorch.org/whl/cu121
uv pip install unsloth
uv pip install jupyterlab datasets trl peft accelerate bitsandbytes
```

### Test dependencies

```sh
python -c "import torch; print('CUDA available:', torch.cuda.is_available()); print('GPU:', torch.cuda.get_device_name(0) if torch.cuda.is_available() else 'None')"
```

