# short-pipe-v1
short reads, standard scheme, nt database (IMG/VR)

Pipeline Directory Structure:
-----------------------------
- raw_reads/            # Place your raw FASTQ files here
- results/              # All pipeline outputs will be stored here
  - fastqc/             # FastQC reports
  - trimmed_reads/      # Trimmed reads from Trim Galore
  - kraken2/            # Kraken2 outputs
  - viral_reads/        # Viral reads filtered by KrakenTools
  - assemblies/         # Contigs assembled by SPAdes
  - centrifuge/         # Centrifuge taxonomical classification results
  - deepvirfinder/      # DeepVirFinder predictions
  - virsorter2/         # VirSorter2 outputs
  - reports/            # Final reports for each sample
- config/               # Configuration files (e.g., config.yaml, subenvironments)
- scripts/              # Custom scripts (e.g., generate_report.py)
- tools/	              # External tools (KrakenTools, DeepVirFinder)
- setup_workplace.sh    # Bash script to expand the workplace ready to go
- setup_environment.sh  # Bash script to install the env
- Snakefile

Steps to Run the Pipeline:
--------------------------
1. Place raw reads in 'raw_reads/' folder, named as '<sample>_R1_001.fastq.gz' and '<sample>_R2_001.fastq.gz'.
2. Update 'config/config.yaml' with your sample names, database paths, and thread settings.
3. Activate the pipeline environment:
   mamba activate virpipe_short1
4. Run the pipeline with:
   snakemake --cores <number_of_cores> --use-conda 
