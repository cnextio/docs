# 🐍 IPython Kernel

By default CNext will run an ipython kernel corresponding to your current environment.

To use the ipython kernel in another virtual environment, you need to follow these steps:

**Step 1**: Activate the python environment you want to use. For example:

```bash
conda activate myEnv
```

**Step 2**: Install ipython

```bash
conda install -c anaconda ipykernel
```

**Step 3**: Create a new ipython kernel spec

```bash
python -m ipykernel install --user --name=myEnv
```

**Step 4**: Deactivate the current virtual environment

```bash
conda deactivate myEnv
```
