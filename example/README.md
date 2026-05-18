# Dataset Examples

Examples are organized by dataset. The Replogle workflow is under `example/replogle/`.

The default local layout used by the Replogle notebooks is:

```text
data/replogle/
  perturb_data/
    finetune_data/nadig_processed_data/replogle.h5ad
    selected_genes/
    gene_names/
    indices_cache/
    meta_data/

checkpoints/replogle/
  from_scratch_replogle.ckpt
```

Recommended order:

1. `replogle/00_download_data.ipynb`
   Download the Replogle subset, required metadata, gene embeddings, and the official checkpoint.

2. `replogle/01_inspect_and_prepare_data.ipynb`
   Inspect the `.h5ad` file, required `obs` columns, the `X_hvg` input space, and a small cell-set tensor.

3. `replogle/02_inference_sampling.ipynb`
   Run one sampling batch with the official `from_scratch_replogle.ckpt`.

4. `replogle/03_debug_training_and_mmd_ablation.ipynb`
   Run 50-step debug training and an `optimization.MMD_loss_factor=0.0` ablation.

Workflow:

```text
Replogle h5ad
  -> obs/obsm inspection
  -> 2,000 HVG cell-set tensor
  -> checkpoint inference
  -> debug training
  -> MMD ablation
```
