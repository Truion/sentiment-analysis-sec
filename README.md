# sec-sentiment
Sentiment analysis of SEC filings based on the lazy prices paper (link here: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=1658471). 
According to the paper, alpha is generated by shorting companies that make an active change in their reporting practices and buying "non-changes". 

This repo implements this paper in an automated way.

As an aside, this repo contains a ETL pipeline to download and clean SEC filings of your choice for natural language processing. You can use that code to process SEC filings and do your own analysis. 

### Directory Structure:
**code:** code to implement the lazy prices paper
  
  _get_sec_filings_df.ipynb_ - code to download raw SEC filings
  
  _clean_and_filter_data.ipynb_ - clean SEC filings, with implementation taken from this paper: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2870309
  
  _calc_doc_similarity.ipynb_ - Preprocesses filing to calculate the document similarity of the latest filing vs the previous filing of the same kind. E.g. Q3 10Q 2018 compared against Q3 10Q 2017. Filings are also processed with stopwords taken from LoughranMcDonald Master Dictionary

**data**: contains cik ticker list, which is used to find CIK number by company name

**master-dict:** contains LoughranMcDonald Master Dictionary and documentation

**sec-filings-downloaded:** contains downloaded SEC filings, with each company having its own folder. The processed cleaned filings are stored in a sub folder named "cleaned_filings"

**sec-filings-index:** index of all SEC filings which is used to download the actual filings 


### Implementation
1) Change "_ProjectDirectory.py_" file to point to your own directory 

2) Run "_get_sec_filings_df.ipynb_" to download raw SEC filings

3) Run "_clean_and_filter_data.ipynb_" to clean raw filings and input them in the appropriate folders

4) Run "_calc_doc_similarity.ipynb_" to process the cleaned data (exclude stopwords, stem if you want), and calculate YoY document similarity for each company


### Package requirements
1) edgar: https://pypi.org/project/edgar/
2) pathlib2
3) tqdm
4) nltk
5) sklearn

### Credits

Members:
Aditya Soni
Akshat Jain
Bhavsaar Saahil
Jaimin Gajjar
Jayant Kataria
Joel Thomas
Mohit Mathuria
