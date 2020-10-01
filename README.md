# PopIns2_snakeproject

Download this PopIns2 snakeproject via

```
git clone https://github.com/Krannich479/PopIns2_snakeproject.git
```

Adjust the variables in `scripts/snake_config.yaml` to your system environment and create some, for this particular snakemake pipeline, required subfolders via

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
