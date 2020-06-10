# ASWW2

## Models
The BERT models are too large to upload to this repo, so you will need to install them separately from github.com/google-research/bert. We primarily used the uncased base model.

## Example Scripts

To run the provided scripts, bert-as-service must be installed. This requires a version of tensorflow >=1.10 and <2.0. We used 1.15.

After installing both the server and client as specified at https://github.com/hanxiao/bert-as-service, start the service as follows:

bert-serving-start -model_dir [PATH TO MODEL] -num_worker=4 -max_seq_len=25

Feel free to adjust num_worker and max_seq_len as you see fit. By default, max_seq_len is 25, but can be a maximum of 512. However, the larger this is, the slower it will run, so try to make it match the longest sequence length you plan to work with.

You should now be able to run the provided notebooks.
