# Matched Pairs Prove Robust Against Inter-Assay Noise

## Abstract
The data-hungry nature of machine learning models has spurred interest in combining data
across assays. Landrum and Riniker have recently shown that combining these in a naive way
results in significant noise, which can be reduced by stringently matching assay metadata.
While it is common knowledge in the field that absolute values from different assays are often
not comparable, it is generally believed that trends or differences will hold. In an effort to
validate or invalidate that assertion, we conduct a matched pair analysis across different assays
and compare how the potency differences vary between assays. We find that inter-assay
potency differences are smaller for matched pairs than for individual compounds, which
indicates that the assay noise observed between individual compounds is at least partially
caused by scaffold-level effects. As was the case for individual compounds, matching assay
data further improved inter-assay agreement at the cost of dataset size. In 44-46% of cases
minimally curated compound pairs agreed within 0.3 pChEMBL units (derived from either K<sub>i</sub> or
pIC<sub>50</sub>), improving to 66-79% after curation, while 12-15% of the compound pairs exhibited a
difference of more than one pChEMBL unit, moving to 6-8% after extensive curation. Our
analysis provides valuable guidance to practitioners in the field and may be useful for the
development of delta-models, aiming to predict property differences between compounds.

## Code

You can replicate the analysis and generate the figures from the paper using the `ChEMBL32_MatchedPairsAnalysis.ipynb` notebook. For the `gather_data` step, you need access to a copy of the ChEMBL32 database via `PostgreSQL`. You can find the database here: [ChEMBL32 database](http://doi.org/10.6019/CHEMBL.database.32). Download the `chembl_32_postgresql.tar.gz`, which includes basic setup instructions.

This step is optional because the relevant data is cached and provided with this repository. However, without access to the database, you won't be able to experiment with custom data curation settings.

### Installation Instructions

1. Create the conda environment:
   ```bash
   conda env create -f environment.yml
   ```

2. Activate the conda environment:
   ```bash
   conda activate chembl_matchedpairs
   ```

3. Launch the Jupyter Notebook:
   ```bash
   jupyter-notebook ChEMBL32_MatchedPairsAnalysis.ipynb
   ```

If you have a `PostgreSQL` database setup for ChEMBL32, update the `connection_string` on line 8 of Cell 1.1 with your database link.

If you do not have the database setup, skip running Cell 1.1 and any cells using the `gather_data` function. All other cells should work as intended.

