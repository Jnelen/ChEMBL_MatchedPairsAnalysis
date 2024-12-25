# Matched Pairs Prove Robust Against Inter-Assay Noise

## Abstract
Machine learning models for chemistry require large datasets, often compiled by combining data from multiple assays. However, combining data without careful curation can introduce significant noise. While absolute values from different assays are rarely comparable, trends or differences between compounds are often assumed to be consistent. This study evaluates that assumption by analyzing potency differences between matched compound pairs across assays and assessing the impact of assay metadata curation on error reduction. We find that potency differences between matched pairs exhibit less variability than individual compound measurements, suggesting systematic assay differences may partially cancel out in paired data. Metadata curation further improves inter-assay agreement, albeit at the cost of dataset size. For minimally curated compound pairs, agreement within 0.3 pChEMBL units was found to be 44-46% for K<sub>i</sub> and IC<sub>50</sub> values respectively, which improved to 66-79% after curation. Similarly, the percentage of pairs with differences exceeding 1 pChEMBL unit dropped from 12-15% to 6-8% with extensive curation. These results establish a benchmark for expected noise in matched molecular pair data from the ChEMBL database, offering practical metrics for data quality assessment.  

## Code

You can replicate the analysis and generate the figures from the paper using the `ChEMBL32_MatchedPairsAnalysis.ipynb` notebook. For the `gather_data` step, you need access to a copy of the ChEMBL32 database via `PostgreSQL`. You can find the database here: [ChEMBL32 database](http://doi.org/10.6019/CHEMBL.database.32). Download the `chembl_32_postgresql.tar.gz`, which includes basic setup instructions. After, you should fill in the connection_string, at the top of the gather_data function. If you have setup the chembl_32 database locally, the connection_string should have the following format:
```python
connection_string = f"postgresql://username:password@localhost:5432/chembl_32"
```

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

