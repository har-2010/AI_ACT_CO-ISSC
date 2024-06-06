# CO-ISSC: Core Ontology-based Incremental Semi-Supervised Clustering

The CO-ISSC pipeline combines, in an incremental process, a semi-supervised dimension reduction technique (semi-supervised UMAP) and a semi-supervised clustering method (adapted C-DBSCAN). Additionally, it uses two types of prior knowledge: (1) a PLM, and (2) a core ontology. The figure below shows its architecture. The CO-ISSC pipeline is evaluated using the AI Act text and the AI Act benchmark.


<div align=center> 
<img src="./CO-ISSC/pipeline.png" width = 75%>
</div> 

# Project Structure

This project includes the three files:

 1. AI ACT Core ontology.
 2. The AI ACT terminology including 900 terms that have been extracted, filtered, and manually classified according to AI Act core concepts.
 3. Source code and dataset:
   
 ##  Below is the organization of the code.
``` 
├── Data : dataset
├── helpers 
│   └── Term
│   │   └── CoreConcept.py : class of core concept extending Term class
│   │   └── Term.py :  class of Term 
│   │   └── Vocabulary.py: vocabulary with terms and CoreConcept
│   └── CDBSCAN.py : adaptation of CDBSCAN
│   └── Corpus.py : the corpus class with vocabulary
│   └── Cosine.py : the SMBM implementation
│   └── Model.py : pipeline 
├── Model : SentencBERT configurations, not needed
├── tools : tool functions to exact terms.
├── prosition.ipynb : main notebook 
└── mytest.ipynb : testing notebook
```

## Major Algorithms/Libraries

* [SentenceBERT](https://sbert.net/) : a powerful model designed for generating semantic sentence-level(not word-level) embeddings for every term and core concept. As the terms can be multi-words, we choose SentenceBERT as the PLM for the pipeline. The dimension of output embedding is 384, rather than 768 like in BERT.

* [Umap](https://umap-learn.readthedocs.io/en/latest/) : a dimension redution algorithm maintaining well both the global and local structure. In this pipeline, dimension is reduced from 384 to 10.

* CDBSCAN: constraint based DBSCAN, introducing two kind of constraints, *Must-link* and *Cannot-link*. We adapted it from [base version](https://link.springer.com/content/pdf/10.1007/978-3-540-72530-5_25.pdf) to fit the core concept based clustering. At each iteration it receives the reduce embedding and clusters the terms leveraging the Core Concepts.

* [SMBM](doi/10.1145/3106426.3109052) : as introduced in the paper, cosine distance is used to weigh the  similarity between each term to core concepts.

## Getting started
Before launching the code, you should step into the source code directory and install necessary pakages as listed in [requirements.txt](./CO-ISSC/requirements.txt).
```bash
pip install -r requirements.txt
```

Then, open the file [proposition.ipynb](./CO-ISSC/proposition.ipynb) and run it.

Also, you can see all the experiments conducted in [mytest.ipynb](./CO-ISSC/mytest.ipynb) on the two corpora: AI ACT corpus and Computer Science corpora.  

Among these experiments, you can find the content of ecah cluster. In addition, for each iteartion setting a stacked hitogram is provided describing the distribution of clusters in each class. In the following two histograms, one is about the the AI ACT corpus and the second is about the Computer Science corpora.



tO ADD the HITOGRAMS
Distribution of clusters in ecah class for Computer Science
tO ADD the HITOGRAMS
Distribution of clusters in ecah class for AI ACT





