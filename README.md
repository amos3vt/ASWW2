# ASWW2

## BERT
For information on how to get started with BERT, please read our BERT guide!

Note that the BERT models are too large to upload to this repository, so you will need to install them separately from https://github.com/google-research/bert. We primarily used the uncased base model.

### Using bert-as-service
Install both the server and client as specified at https://github.com/hanxiao/bert-as-service. These will require a version of tensorflow >=1.10 and <2.0. We used 1.15.

Before running a notebook that uses bert-as-serice, run the following command:

 - bert-serving-start -model_dir [PATH TO MODEL] -num_worker=4 -max_seq_len=25

Feel free to adjust num_worker and max_seq_len as you see fit. By default, max_seq_len is 25, but can be a maximum of 512. However, the larger this is, the slower it will run, so try to make it match the longest sequence length you plan to work with.

### Using Sentence-BERT
Follow instructions for installation here: https://github.com/UKPLab/sentence-transformers

If installed correctly, notebooks using Sentence-BERT should run properly.

## Tag Matching
A variety of tags were given to the transcribed documents, a subset of which were designated "expert" tags. The purpose of our tag matching script was to match each transcriber tag with the most closely related expert tag.

The embeddings for each transcriber tag were compared to the embeddings of the expert tags. Each pairing was ranked by cosine simialrity, and the top three expert tag matches for each transcriber tag were stored. We used Sentence-BERT for getting tag embeddings, since their model is more fine-tuned for semantic textual similarity.

This notebook can be found under scripts/TagApprox_SentenceBert.ipynb and the resulting matches at data/tag_approx_space.csv.

### Previous Implementation
Previously, we implemented this using bert-as-service. However, we found that the resulting matches were often more lexically similar than semantically similar. You can find this notebook under scripts/TagApprox.ipynb, and an Excel file containing the resulting matches at data/tag_approx_space.xlsx.
