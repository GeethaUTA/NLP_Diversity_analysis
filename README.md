# NLP_Diversity_analysis
# Data Preprocessing
This Python function filter_rows_and_matching_words_unique_words appears to filter rows from a dataset based on matching words found in the company names from the S&P 500 dataset. Let's break down the code step by step:

Drop Rows with Missing Values:

sp500_data = sp500_data.dropna(subset=['Company']): Drops rows from the S&P 500 dataset (sp500_data) where the 'Company' column has missing values.
Decode Company Names:

your_dataset = decode_company_names(your_dataset): Applies a function decode_company_names to decode company names in your dataset (your_dataset).
Define Common Words to Exclude:

A set of common words to exclude from consideration is defined, such as articles like 'the', 'a', 'an', and conjunctions like 'and', etc.
Extract Unique Words from S&P 500 Company Names:

Unique words are extracted from the company names in the S&P 500 dataset, excluding common words.
Each company name is split into words, converted to lowercase, and added to a set to ensure uniqueness.
Create Empty DataFrame for Result:

An empty list result_data is created to store filtered rows and corresponding matched words.
Iterate Through Each Row in Your Dataset:

For each row in your dataset:
The company name (assuming it's stored in the column 'company_name') is extracted.
The company name is split into words, converted to lowercase.
The intersection of words in the company name and S&P 500 words is computed.
If there are matching words, the row along with the matched words is added to result_data.
Create DataFrame from Result Data:

Finally, a DataFrame result_df is created from result_data with appropriate column names, including the original columns from your_dataset and an additional column for matched words.
Return Result DataFrame:

The resulting DataFrame containing filtered rows and corresponding matched words is returned.
This function essentially filters rows from your_dataset based on whether their company names contain words that match with those in the S&P 500 company names, excluding common words. It then returns a DataFrame containing the filtered rows along with the matched words.



# NLP for extracting diversity related keywords:
Import Libraries:

import pandas as pd: Imports the Pandas library with the alias pd.
import spacy: Imports the SpaCy library for natural language processing.
Load Language Model:

nlp = spacy.load("en_core_web_sm"): Loads the English language model from SpaCy. This model provides pre-trained word vectors and several linguistic annotations.
Define Diversity Keywords:

A list of keywords related to diversity, inclusion, and related concepts is defined. These keywords are used to identify relevant terms in the text data.
Define Batch Size:

batch_size = 2000: Sets the batch size for processing text data. Larger datasets may require larger batch sizes to efficiently process the data.
Process Text Data in Batches:

A loop is used to process the text data in batches.
for batch_start in range(0, len(df5_nlp), batch_size):: Iterates over the indices of the text data DataFrame (df5_nlp) in steps of batch_size.
batch_end = min(batch_start + batch_size, len(df5_nlp)): Calculates the end index of the current batch, ensuring it does not exceed the length of the DataFrame.
batch = df5_nlp.loc[batch_start:batch_end]: Retrieves the batch of data from the DataFrame based on the start and end indices.
Process Each Row in the Batch:

For each row in the batch, the text in the column 'review_pros__DUPLICATE' is processed using the SpaCy language model.
The lemma (base form) of each token in the text is extracted, and if the lemma is present in the diversity keywords list, it is retained.
The filtered tokens are then joined together into a string separated by commas and stored in a new column 'filtered_words' in the DataFrame.
Print DataFrame:

After processing all batches, the updated DataFrame df5_nlp is printed, showing the original data along with the added column 'filtered_words' containing filtered tokens
