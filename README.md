# ASWW2

## Example Scripts

To run both the Performance and WordOrder notebooks, bert-as-service must be installed. Bert-as-service requires a version of tensorflow >=1.10 and <2.0.

After installing both server and client as specified at https://github.com/hanxiao/bert-as-service, start the service before opening the notebooks. I used the following (but you can adjust this as you see fit):

bert-serving-start -model_dir [PATH TO MODEL] -num_worker=4 -max_seq_len=100

By default, the max_seq_len is 25, and can have a maximum of 512. However, the larger this is, the slower it will run, so try to make it match the longest sentence length you plan to work with.

Make sure that you use the EXACT path to whichever model (cased/uncased, base/large) you use.
