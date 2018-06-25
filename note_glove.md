## Try Standford Official Glove
- https://github.com/stanfordnlp/GloVe

### research-gpu-testing [~/work/glove] -wayne- build/vocab_count -min-count 5 -verbose 2 < pixnet_10000.txt > vocab_10000.txt
```
BUILDING VOCABULARY
Processed 4849198 tokens.
Counted 405190 unique words.
Truncating vocabulary at min count 5.
Using vocabulary of size 73720.
```

### research-gpu-testing [~/work/glove] -wayne- build/cooccur -memory 4.0 -vocab-file vocab_10000.txt -verbose 2 -window-size 15 < pixnet_10000.txt > cooccurrence.bin
```
COUNTING COOCCURRENCES
window size: 15
context: symmetric
max product: 13752509
overflow length: 38028356
Reading vocab from file "vocab_10000.txt"...loaded 73720 words.
Building lookup table...table contains 95909693 elements.
Processed 4849198 tokens.
Writing cooccurrences to disk.........3 files in total.
Merging cooccurrence files: processed 52216526 lines.
```

### research-gpu-testing [~/work/glove] -wayne- build/shuffle -memory 16.0 -verbose 2 < cooccurrence.bin > cooccurrence.shuf.bin
```
SHUFFLING COOCCURRENCES
array size: 1020054732
Shuffling by chunks: processed 52216526 lines.
Wrote 1 temporary file(s).
Merging temp files: processed 52216526 lines.
```

### research-gpu-testing [~/work/glove] -wayne- build/glove -save-file vectors -threads 32 -input-file cooccurrence.shuf.bin -x-max 100 -iter 20 -vector-size 100 -binary 2 -vocab-file vocab_10000.txt -verbose 2
```
TRAINING MODEL
Read 52216526 lines.
Initializing parameters...done.
vector size: 100
vocab size: 73720
x_max: 100.000000
alpha: 0.750000
06/21/18 - 12:14.21AM, iter: 001, cost: 0.015291
06/21/18 - 12:14.41AM, iter: 002, cost: 0.011456
06/21/18 - 12:15.00AM, iter: 003, cost: 0.010210
06/21/18 - 12:15.20AM, iter: 004, cost: 0.009468
06/21/18 - 12:15.37AM, iter: 005, cost: 0.008938
06/21/18 - 12:15.54AM, iter: 006, cost: 0.008513
06/21/18 - 12:16.11AM, iter: 007, cost: 0.008159
06/21/18 - 12:16.29AM, iter: 008, cost: 0.007857
06/21/18 - 12:16.46AM, iter: 009, cost: 0.007598
06/21/18 - 12:17.06AM, iter: 010, cost: 0.007366
06/21/18 - 12:17.24AM, iter: 011, cost: 0.007160
06/21/18 - 12:17.40AM, iter: 012, cost: 0.006975
06/21/18 - 12:17.58AM, iter: 013, cost: 0.006806
06/21/18 - 12:18.15AM, iter: 014, cost: 0.006652
06/21/18 - 12:18.36AM, iter: 015, cost: 0.006512
06/21/18 - 12:18.53AM, iter: 016, cost: 0.006384
06/21/18 - 12:19.14AM, iter: 017, cost: 0.006266
06/21/18 - 12:19.31AM, iter: 018, cost: 0.006158
06/21/18 - 12:19.50AM, iter: 019, cost: 0.006058
06/21/18 - 12:20.11AM, iter: 020, cost: 0.005966
```
