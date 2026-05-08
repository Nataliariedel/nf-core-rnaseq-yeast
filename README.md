RNA-seq Analysis: Saccharomyces cerevisiae
This project contains the configuration and execution of the nf-core/rnaseq pipeline in a local environment using WSL2 (Windows Subsystem for Linux).

The analysis processes RNA-sequencing data from Saccharomyces cerevisiae to generate gene expression counts ready for downstream differential expression analysis.

- Tech Stack
Nextflow: Workflow orchestrator for scalability and reproducibility.

Docker: Containerization of all bioinformatics tools (FastQC, STAR, Salmon, etc.).

VS Code: Primary IDE integrated with WSL2 for environment management.

Hardware: Executed on a local machine with limited resources (8GB RAM / 4 CPUs).

- Pipeline Details
  
Pipeline: nf-core/rnaseq

Reference Genome: R64-1-1 (S. cerevisiae)

Platform: Ubuntu 22.04 on WSL2.

- Challenges & Solutions: Resource Optimization
The main challenge of this project was running a high-performance computing (HPC) pipeline on consumer-grade hardware. Standard nf-core configurations often require 12GB+ of RAM per process, leading to crashes in local environments.

Key solutions implemented:

Custom Configuration: Created a custom.config file to override default resource allocations.

Process Labeling: Redefined process_low, medium, and high labels to fit within a 6GB RAM ceiling.

Specific Overrides: Forced memory-intensive tasks like FQ_LINT and FASTQC to operate with 4GB and 1 CPU, ensuring pipeline stability without compromising data integrity.

- Project Structure
samplesheet.csv: Input metadata and FastQ file paths.

custom.config: Tailored resource management settings for local execution.

results/: Contains the MultiQC report and gene quantification matrices (Salmon/STAR).

- Results
The pipeline successfully generated:

Quality Control reports via MultiQC.

Alignment files (BAM) and Quantification tables (counts/TPM) for further statistical analysis.
