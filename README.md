## README

This notebook does 1 thing:

- Load CLIP v1.0 in a Python 3.7.0 virtual environment.
- Compute natural language embeddings for tokens of interest using the CLIP transformer model.

_CLIP is the *Contrastive Language-Image Pre-Training* neural network trained on a variety of (image, text) pairs, first reported by Radford et al (2020) and applied by Hessel et al (2021). <BR>
In principle, given an image, CLIP can be instructed in natural language to predict the most relevant text snippet, without directly optimizing for the task, similarly to the zero-shot capabilities of GPT-2 and 3._

### Guidelines

This iPython notebook must be run in a Python virtual environment, running Python v3.7.0. This is a prerequisite so the proper versions of Torch 1.7.0+cpu and TorchVision 0.8.1+cpu can be invoked to run the CLIP 1.0 inference engine. Instructions to install CLIP are provided below for Linux hosts, assuming that:

- your interactive terminal session executes a Bourne shell (`sh`) or a Bourne derivative ( `ksh`, `bash`, ...).
- you already set up a Python 3.7.0 virtual environment, in directory `/path/to/my_directory`.
- you know how to handle CLI in terminal.

#### Setting up and registering a custom iPython kernel

What follows applies to CPU-only constrained installations. For CUDA-enabled machines, refer to `https://github.com/OpenAI/CLIP`.

- Assuming you have configured `pyenv` (on your favorite Linux host) to manage multiple Python virtual environments with specific package requirements, choose the directory in which to setup your Python virtual environment and install your iPython kernel utility package `ipykernel`:

```
      $ cd /path/to/my_directory
      $ pyenv local 3.7.0
      $ python -m pip install ipykernel
```
- Install every required packages in the virtual environment directory `/path/to/my_directory` (see following section for that).

```
      $ python -m pip install torch==1.7.0+cpu torchvision==0.8.0+cpu torchaudio==0.7.0 -f https://download.pytorch.org/whl/torch_stable.html
      $ python -m pip install ftfy regex tqdm
      $ python -m  pip install git+https://github.com/openai/CLIP.git
```

- Make the new custom iPython kernel, clip1.0, available in interactive Python sessions:
```
      $ cd /path/to/my_directory
      $ ipython kernel install --user --name clip1.0 --display-name "Python3.7.0 (clip1.0)"
      $ jupyter notebook        # launch an iPython session
```

- Select the special virtual environment kernel ***Python 3.7.0 (clip1.0)*** under the `New notebook` button in the top-right region of the browser page.


### Package requirements

Package requirements are detailed below. For a quick demo also install `Pillow==8.2.0` and dependencies.

- Install all required packages in the virtual environment directory "/path/to/my_directory", with:
```
    $ cd /path/to/my_directory
    $ python -m pip install <<- 'EOF'
                clip @ git+https://github.com/openai/CLIP.git@04f4dc2ca1ed0acc9893bd1a3b526a7e02c4bb10ftfy
                Cython==0.29.22
                ftfy==6.0.3
                ipykernel==5.5.3
                ipyparallel==6.3.0
                ipython==7.22.0
                ipython-genutils==0.2.0
                ipywidgets==7.6.3
                nltk==3.6.5
                numpy==1.18.5
                regex==2021.10.8
                torch==1.7.0+cpu
                torchaudio==0.7.0
                torchvision==0.8.1+cpu
                tqdm==4.61.1
                scipy==1.6.2
    EOF
```
