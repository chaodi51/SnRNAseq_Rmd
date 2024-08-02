# Ocular snRNA-seq Project

## Project Overview

This project focuses on the single-nucleus RNA sequencing (snRNA-seq) analysis of ocular samples to study glaucoma and other related diseases. The project utilizes various bioinformatics tools and workflows to process and analyze the sequencing data, with a significant emphasis on data visualization and interpretation.

## Directory Structure
```
Ocular_snRNA-seq
├── src
│ ├── 20231015_snRNAseq_NHP_runs_1_3_4_integrated_analysis_Kamil.rmd
│ ├── Ocular_snRNAseq_pilot_3rd.rmd
│ ├── Ocular_snRNAseq_pilot.rmd
│ ├── Ocular_snRNAseq_macula_comp_dissections.rmd
│ ├── Ocular_snRNAseq_pilot_combined.rmd
│ ├── Ocular_snRNAseq_RGC_NEFH-GFP_macula.rmd
│ ├── Ocular_snRNAseq_RGC_NEFH-GFP_integrate_periphery_Newmacula_reps.rmd
│ ├── Ocular_snRNAseq_macula_periphery_Wunsorted.rmd
│ ├── Ocular_snRNAseq_Photoreceptor_CAG_GRK1-GFP_integrated.rmd
│ ├── Ocular_snRNAseq_macula_periphery_Wunsorted_MasFas5_Truseq_Ref.rmd
│ ├── Ocular_snRNAseq_macula_periphery.rmd
│ ├── Ocular_snRNAseq_Aflibercept_NHP_1.rmd
│ ├── Ocular_snRNAseq_Photoreceptor_CAG_GRK1-GFP.rmd
│ ├── Ocular_snRNAseq_NEFH-CAG_GFPplus_allFiveMaculas.rmd
│ ├── Ocular_snRNAseq_RGC_NEFH-GFP_periphery.rmd
│ ├── Ocular_snRNAseq_RGC_NEFH-GFP_integrate_macula_periphery_Newmacula.rmd
│ ├── Ocular_snRNAseq_macula_periphery_integration.rmd
│ ├── Ocular_snRNAseq_NEFH-CAG_GFPplus_integrate_3maculas.rmd
│ ├── Ocular_snRNAseq_hSC_RPE_NRF2_dryAMD.rmd
│ ├── Ocular_snRNAseq_pilot_unsorted.rmd
│ ├── Ocular_snRNAseq_Aflibercept_NHP_2.rmd
│ ├── Ocular_snRNAseq_pilot_4th.rmd
│ ├── Ocular_snRNAseq_NEFH-CAG_GFPplus_twoNewMacula.sh
│ ├── Ocular_snRNAseq_NEFH-CAG_GFP_integrate_3maculas.rmd
│ └── Ocular_snRNAseq_NEFH-CAG_GFPplus_twoNewMacula.rmd
├── data
│ ├── nf-core
│ └── raw_data
│ └── 240426_A01959_0054_BHVH2HDMXY
├── configs
│ ├── samples.txt
│ └── samplesheet_local.csv
├── docs
├── README.md
└── reqs
```

## Setup Instructions

### Prerequisites

Ensure you have the following software installed:
- [Conda](https://docs.conda.io/en/latest/miniconda.html)
- [R](https://www.r-project.org/)
- [Seurat](https://satijalab.org/seurat/)
- [Bioconductor](https://www.bioconductor.org/)

### Installation

1. **Clone the repository**:
   ```sh
   git clone https://github.com/your-repo/Ocular_snRNA-seq.git
   cd Ocular_snRNA-seq
2. **Setup Conda Environment**:
Create and activate a Conda environment with the necessary dependencies:
```sh
conda create -n ocular_snRNA-seq_env r-essentials r-base
conda activate ocular_snRNA-seq_env
```

3. **Install R Packages**:
Install the required R packages listed in the .rmd files:

```r
install.packages(c("Seurat", "dplyr", "ggplot2", "patchwork"))
BiocManager::install(c("biomaRt", "scater"))
```

4. **Prepare Data**:
Ensure raw data is located in data/raw_data/{run}/

## Usage

### Running the Analysis
Execute the RMarkdown files to perform the analysis. For example, to run the integrated analysis:

```sh
## raw data processing using nf-core Nextflow pipeline /mnt/data/apps/nf-core/scrnaseq
bash src/Ocular_snRNAseq_NEFH-CAG_GFPplus_twoNewMacula.sh
## downstream analysis including QC, filtering, integration, Clustering, cell type annotation, 
## differential expression, marker gene expression visualizations etc.
Rscript -e "rmarkdown::render('src/Ocular_snRNAseq_NEFH-CAG_GFPplus_twoNewMacula.rmd')"
```

### Example Commands
Run a specific RMarkdown analysis file:

```sh
Rscript -e "rmarkdown::render('src/Ocular_snRNAseq_pilot.rmd')"
```

## Contributing

Contributions are welcome! Please fork the repository and submit pull requests. For major changes, please open an issue first to discuss what you would like to change.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Contact

For any questions or issues, please open an issue on GitHub or contact chao.di@sparktx.com.