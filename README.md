# CO-ISSC:Core Ontology-based Incremental Semi-Supervised Clustering

This is the pipeline we are going to pulish on KES 2024 conference, with a core ontology as prior knowledge, combined with UMAP and adapted C-DBSCAN.

<div align=center> 
<img src="./CO-ISSC/pipeline.png" width = 75%>
</div> 

# Project Structure

This project includes the three files:
 the tow files that I have already added (i wil explain the content of these two files), 
 1. file 1
 2. file 2
 3. source code and dataset:
   
   Below is the organization of the code.
``` bash
├── Data : dataset
├── helpers 
    └── Term
        └── CoreConcept.py : core concept extend Term class
        └── Term.py :  class Term and its funciton
        └── Vocabulary.py: vocabulary with terms and CoreConcept
    └── CDBSCAN.py : adaptation of CDBSCAN
    └── Corpus.py : the corpus class with vocabulary
    └── Model.py : pipeline 
├── Model : SentencBERT configurations, not needed
├── tools : tools function to exact terms.
├── prosition.ipynb : main notebook 
├── mytest.ipynb : test notebook
```

## Getting started
Before launching the code, you should step into the source code directory and install neccesary pakages as listed in [requirements.txt](./CO-ISSC/requirements.txt).
```bash
pip install -r requirements.txt
```

Then, Open the file [proposition.ipynb](./CO-ISSC/proposition.ipynb) and run it.

Also, you can see all the experiments conducted in [mytest.ipynb](./CO-ISSC/mytest.ipynb)





