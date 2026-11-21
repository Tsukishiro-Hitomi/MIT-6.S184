# MIT 6.S184 notebook environment (Windows)

This workspace uses Python 3.12 in `.venv` and the Jupyter kernel `mtds` (displayed as **MIT 6.S184 (mtds)**). The environment has JupyterLab, ipykernel, NumPy, Matplotlib, seaborn, scikit-learn, einops, celluloid, tqdm, and CUDA-enabled PyTorch/torchvision.

The machine already had PyTorch 2.13.0+cu126 and torchvision 0.28.0+cu126 installed under its Python 3.12 installation. `.venv/pyvenv.cfg` has `include-system-site-packages = true` to reuse these large CUDA packages rather than downloading a second copy; this environment is therefore not completely isolated from global packages. Project-local packages take precedence. On a different computer, install a compatible PyTorch/torchvision pair and other requirements separately rather than copying `.venv`.

## Open notebooks

From PowerShell in this directory:

```powershell
.\.venv\Scripts\jupyter-lab.exe
```

Alternatively, open this folder in VS Code, install the Microsoft Python and Jupyter extensions if prompted, open a `.ipynb` file and select **MIT 6.S184 (mtds)** as its kernel. All three notebooks already reference the `mtds` kernel, so no notebook edits are needed.

Check the kernel:

```powershell
.\.venv\Scripts\python.exe -c "import torch, torchvision, seaborn, sklearn, einops, celluloid; print(torch.__version__, torch.cuda.is_available())"
```

`lab_three.ipynb` downloads MNIST to `./data` on first run and requires internet access. Its later cells explicitly use CUDA. These course notebooks contain unfinished exercises and long training runs; environment checks cannot guarantee every cell completes before the exercises are implemented. `requirements.txt` lists the dependencies for setting up another machine; a matching GPU-specific PyTorch build must be selected for that machine.
