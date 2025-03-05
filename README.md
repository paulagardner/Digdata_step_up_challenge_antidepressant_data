
# Starting the python path: Introduction to Google colab
## Starting resources

•	If you are new to google colab you can watch an introduction to it here - https://www.youtube.com/watch?v=inN8seMm7UI 

•	If you have never used python before you can read an introduction to the language here - https://www.w3schools.com/python/python_intro.asp 

## Setting up google colab 
You will have more details for setting up google colab in your We Transfer file in the document 'Google colab intro'

1.	You should have access to the file ‘Digdata_python_path.ipynb’ in this github repository. Download this to your device somewhere where is accessible.

2.	Navigate to the google colab website

a.	If you have never used google colab before, you will be asked to create an account – which you can do with a pre-existing google account

b.	If you have an account, log in.

 
3.	You will have a set of options, select  ‘Upload’,  and then browse for the file ‘Digdata_python_path.ipynb’ to upload

 
4.	This should successfully load your notebook

a.	Note: whenever you see the symbol circled below, it means you can toggle to hide the section for ease of navigation of the document
 

# Data we are using for analysis

This data is from the NSHBSA Open Data Portal, and is called the 'Prescription Cost analysis' dataset.

https://opendata.nhsbsa.net/dataset/prescription-cost-analysis-pca-monthly-data

This data is open source, which means:

- We can share it openly
- It has no security concerns

This is a monthly dataset that describes how many medicines were prescribed across all GP Practices in england, per NHS Region, and what they cost.
This is 'real data', so actually describes real anti-depressant prescribing in England.
We have merged, simplified and filtered all these monthly files into a single dataset.

The data is being read into this notebook using this github repo link below (do not delete).

## BSA_ODP_PCA_REGIONAL_DRUG_SUMMARY.csv

This dataset contains 6 columns:

*   *YEAR*: The year in the format YYYY. There are 4 years-worth of prescribing information in the dataset.
*   *YEAR_MONTH*: The year and month, in the format YYYYMM, where 202401 is the same as January 2024. There are 46 year-month values in the data.
*   *REGION*: The NHS Region. There are 7 regions in the data.
*   *DRUG*: The name of the anti-depressant medicine. There are 32 of these in the data.
*   *ITEMS*: How many items were prescribed.
*   *COST*: The combined cost for all those items.

In a sentence we could describe this dataset as:

- Per English NHS Region and per year-month, the volume and cost of each antidepressant drug prescribed.

And what we are going to do with this data is:

- Understand national and regional prescribing volumes and costs
- Understand national and regional prescribing trends
- Understand monthly and annual trends
- And finally, maybe even predict future monthly anti-depressant prescribing volumes

### BSA_ODP_PCA_REGIONAL_SUMMARY.csv

So we can see that the original data differs in a few ways:

- It only contains antidepressant drugs
- It doesn't contain BNF Chapter and BNF Section information

The BNF stands for the *British National Formulary*.
The BNF is structured hierarchically into Chapters, Sections and Chemical Substances (Drugs).

For example:

- Amitriptyline hydrochloride is an actual antidepressant *DRUG*
- Amitriptyline hydrochloride is one of many *DRUG* within the 'Antidepressant drugs' *BNF_SECTION*
- Antidepressant drugs is one of many *BNF_SECTION* within the '04: Central Nervous System' *BNF_CHAPTER*
- And there are 23 *BNF_CHAPTER* (although very little prescribing stems from some of the chapters)

In summary, BNF chapters are split into sections, which are then split into actual drugs (i.e. a hierarchy).
