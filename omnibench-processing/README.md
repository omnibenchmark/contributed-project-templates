# {{ name }}
{% if description %}
{{ description }}
{% endif %}
## Dataset template

Template to process raw dataset from omnibenchmark projects. The template assumes that you uploaded dataset to Renku using the [`omnibench_dataset`](https://github.com/ansonrel/contributed-project-templates/tree/main/omnibench-dataset) template or similar project. 

This template explains how to import the desired datasets and process them uniformly before passing them to the methods. As an example, this template shows how to perform normalization, HVG, PCA, TSNE, UMAP on a dummy dataset of the same style as for the `omnibench_dataset`. 

## Steps to process your omnibenchmark data

### 1. Initialize your new project

I. On the Renku page, click *new project*. 

II. In the fields, paste: 

- [omni_data](https://renkulab.io/gitlab/omnibenchmark/omni_data), a similar *omnibenchmark* project group, or your own namespace in `Namespace`,

- `https://github.com/ansonrel/contributed-project-templates` in `Repository URL`,

-  `main` in the `Repository Reference`,

-  `Custom - Basic omnibenchmark processing` as a template. 

III. Start a new environment in the `Environments` tab of your Renku project.

### 2. Process the data

I. If needed, **modify the `process_data.R`** script that processes the data by default with: 

- normalization (`logNormCounts`)

- Identification of top highly variable genes (`getTopHVGs`) 

- Dimension reduction (`runPCA`, `runUMAP`)

II. Fill in the fields in the `src/config.sh`. The most important fields are

- `OMNI_DATA_RAW`, a keyword that should match the tag that you defined in your renku data project(s). 

- `OMNI_DATA_PROCESSED`, the keyword that will be used by the methods to query the processed data. 

III. Run `bash src/process_data.sh`. Once finished, your processed data are uploaded to renku and available for the next step. 

### 3. Running the methods. 

COMING SOON. 


