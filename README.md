# PopIns2_snakeproject

This github project contains a generic [snakemake](https://snakemake.readthedocs.io/en/stable/) pipeline for [PopIns2](https://github.com/kehrlab/PopIns2). It is supposed to facilitate your PopIns2 run and provides examples for a streamlined workflow. Users are encouraged to freely use and modify the code.

---

### Setup

Download this PopIns2 snakeproject via

```
git clone https://github.com/Krannich479/PopIns2_snakeproject.git
```

The top folder _PopIns2_snakeproject_ will be referred as WORK_DIR. This guide assumes that every instruction will be executed from within the WORK_DIR unless stated otherwise. Adjust the variables in `scripts/snake_config.yaml` to your system environment and create some, for this particular snakemake pipeline, required subfolders via

```
mkdir unmapped
mkdir results
```

Create a subfolder per sample within the `unmapped` folder and copy (or rather link!) the mapped reads and their index into the respective sample folder. Your initial folder structure should then look like

```
$ tree .
.
├── README.md
├── results
├── scripts
│   ├── snake_config.yaml
│   └── Snakefile
└── unmapped
    ├── sample_01
    │   ├── sample_01.bam
    │   └── sample_01.bam.bai
    ├── sample_02
    │   ├── sample_02.bam
    │   └── sample_02.bam.bai
    └── sample_03
        ├── sample_03.bam
        └── sample_03.bam.bai
```

Note that in the default setup of this pipeline the sample subfolders `unmapped/<sample_##>` have the same name as the mapping files `unmapped/<sample_##>/<sample_##>.bam`. 

- Explain snake_config

--- 

### Workflow overview

<img src="https://github.com/Krannich479/PopIns2_snakeproject/blob/master/dag.svg" width="700">

The DAG above displays the workflow using three samples (HG00448, HG00449, HG00450). Each module, except for the genotype module, directly reports its output to the _all rule_ and provides the input for the next successive module of PopIns2. 
