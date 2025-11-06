# scCODI
Global and cross-omics feature aggregation improves single-cell multi-omics integration and clustering.

scCODI, a unified cross-omics deep learning framework for robust and interpretable integration of single-cell multimodal data. scCODI comprises two complementary modules that jointly optimize feature fusion and structural alignment. The COFInt module encodes concatenated multi-omics inputs and learns a global cell–cell relation matrix via an attention-guided mechanism to enhance shared representations through structure-aware feature refinement. Building upon this, the GRgCL module enforces cross-modal alignment by performing structure-aware contrastive learning, leveraging the relation matrix to maintain biological proximity and preserve the topology of the cellular manifold. Through this dual-space optimization strategy, scCODI effectively captures both inter-omic complementarity and intra-cell consistency, yielding biologically coherent and structure-preserving embeddings. Extensive experiments on nine paired single-cell multi-omics datasets demonstrate that scCODI consistently outperforms existing methods in integration and clustering tasks, providing a powerful tool for decoding cellular heterogeneity and cross-layer regulatory mechanisms.

![model framwork](https://github.com/Chengchenyang53/scCODI/blob/master/model.png)

# Dependencies
Python 3.8.1

Pytorch 1.6.0

Scanpy 1.6.0

SKlearn 0.22.1

Numpy 1.18.1

h5py 2.9.0

### Setting Up the Environment
1) **Create a virtual environment:**

`conda create -n scCODI python=3.8` 

` conda activate scCODI` 

2) **Install dependencies:**

`pip install -r requirements.txt` 

3) **Update transformer:**

Before run, please carefully read  'S_update_transformer.docs', and refer to the steps inside it to modify the code in order to get S.

# Run scCODI
1) Prepare the input data in h5 format.
   
2) RNA and ATAC : 

`python -u main.py --n_clusters 'num_cluster' --ae_weight_file 'AE_weight_file' --data_file datafile
--save_dir ../result --embedding_file --prediction_file --filter1 --filter2 --f1 2000 --f2 2000 -el 256 128 64 -dl1 64 128 256 -dl2 64 128 256` 

3) RNA and ADT : 

`python -u main.py --n_clusters 'num_cluster' --ae_weight_file 'AE_weight_file' --data_file datafile
--save_dir ../result --embedding_file --prediction_file`

# Output of scCODI
scCODI outputs a latent representation of data which can be used for further downstream analyses and visualized by t-SNE or Umap.

