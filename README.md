# Machine Learning-Based Hypothesis Generation to Select Optimum Additive for Perovskite Single-Crystal Synthesis (PvkAdditives)
This documentation is prepared as the workflow to accompany the following study:

**"(insert the title of the paper)"**

Noor Titan Putri Hartono (1), Mansoor Ani Najeeb Nellikkal (2), Zhi Li (3), Alexander Norquist (2), Joshua Schrier (4), Tonio Buonassisi (1) **DID I MISS ANYONE?**

Affiliations:

1. Massachusetts Institute of Technology, 77 Massachusetts Avenue, Cambridge, Massachusetts 02139, USA
2. Department of Chemistry, Haverford College, 370 Lancaster Avenue, Haverford, Pennsylvania 19041, USA 
3. Molecular Foundry, Lawrence Berkeley National Laboratory, 1 Cyclotron Road, Berkeley, California 94720, USA 
4. Department of Chemistry, Fordham University, 441 E. Fordham Road, The Bronx, New York 10458, USA 

## Installation and Requirements
To install, just clone this repository and chemprop repository:

`$ git clone https://github.com/PV-Lab/PvkAdditives.git`

`$ cd PvkAdditives`

To install the required packages, create a virtual environment using Anaconda/ Miniconda (https://docs.conda.io/en/latest/miniconda.html). The optional but recommended setup on Anaconda/ Miniconda:

`$ conda env create -f environment.yml`

`$ conda activate pvkadditives`

`$ jupyter notebook`

Also download the SMILES database from eMolecules (https://downloads.emolecules.com/free/) for mapping out the chemical space, especially in the planning step.

## Workflow
After measuring the distributions of the sizes of black crystals (MAPbI<sub>3</sub>) using a separate software (recommendation: ImageJ https://imagej.nih.gov/ij/download.html) and measuring the metric of interest (in our case, we measure the top 10<sup>th</sup> percentile of each vial of perovskite single-crystals), we can start analyze the data.

There are X separate Jupyter Notebook for each step of the workflow.
1. `additives_diversity.ipynb` consists of the Tanimoto similarity-based analysis to determine the diversity of the pre-screened additive molecules, and prioritize the synthesis and measurement based on that. The list of additive experimental candidates is in `dataset/20211013_smiles_experimental_candidates_sorted.csv`.
2. `regression_mordred.ipynb` consists the combination of: (a) Mordred featurization (b) Recursive feature elimination (RFE) (c) Random forest regression (d) Shapley feature importance rank, to drive the hypothesis generation. Both round 1 and round 2 of data are analyzed using this notebook. The round 1 data is compiled in  `dataset/20210923_round1_compiledData.csv`, and the round 2 data is compiled in `dataset/20211006_round2_compiledData.csv`.
3. `simulation_boxfunction.ipynb` consists the following: (a) It randomly draws SMILES from the eMolecules database, so we can investigate where our SMILES of interest are in the chemical space using t-SNE.Based on the *n*-randomly drawn SMILES, we can construct the dataset with *x* as our feature of interest (in our case, it's ATSC5Z). Therefore, *f(x) = 1* when the ATSC5Z value of the molecule falls within the range of our 'box', and  *f(x) = 0* otherwise. (b) After constructing both *x* and *f(x)* in our dataset, we can test the sequence of algorithms: Mordred featurization, RFE, random foreset regression, and Shapley feature importance rank to see if ATSC5Z appears as the most important feature.

## Authors
| |  | 
|---|---|
|**Author(s)** | Noor Titan Putri Hartono |
|**Version** | 1.0/ October 2021  |   
|**E-mail(s)**   | noortitan at alum dot mit dot edu  |
| | |

## Attribution
This work is under an Apache 2.0 License. Please, acknowledge use of this work with the appropriate citation to the repository and research article.

## Citation

    @Misc{pvkadditives2021,
      author =   {The Perovskite Additives authors},
      title =    {Machine Learning-Based Hypothesis Generation to Select Optimum Additive for Perovskite Single-Crystal Synthesis},
      howpublished = {\url{https://github.com/PV-Lab/PvkAdditives}},
      year = {2021}
    }