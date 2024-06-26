

# AI for Bioinformatics: Hands-On Exercise

Now it's your turn to try. 

## The Code

You are working on improving an alignment algorithm. Alignments are typically used for comparing samples from individuals to a reference consensus sequence. To make sure things are working, you want to compare the alignment created by an existing function (`pairwiseAlignment`) to an alignment created by your tool (`my_new_Aligner`).

**Note**: This code is just an example and was written strictly for educational purposes.


``` r
if (!requireNamespace("BiocManager", quietly = TRUE))
  install.packages("BiocManager")
if (!requireNamespace("Biostrings", quietly = TRUE))
  BiocManager::install("Biostrings")

library(Biostrings)

reference <- DNAString("ATCGTACGTA")
query <- DNAString("ATCGTAGCTA")

# Perform pairwise sequence alignment
alignment <- pairwiseAlignment(reference, query)

# Perform sequence alignment using your algorithm
my_alignment <- my_new_Aligner(reference, query)

# Compare pairwise alignment to my_alignment
my_evaluation <- my_alignment_evaluator(reference, query, alignment, my_alignment)
```

## Questions

1. Things are going great with the toy data! You decide to make a tiny subset of your data for testing your aligner by copying the top 100 sequences from patient 1. You then submit the aligner and data to Bard. You prompt, "is there anywhere handling this data can be made more efficient?" Why is this problematic?

2. Can AI be used to improve annotation in the code above? Why or why not?

3. You prefer writing loops, but have learned recently that R works more efficiently using `apply()` functions. Is it okay to ask ChatGPT to refactor a small loop into an `apply()` function? Why or why not? 

4. A colleague gives you a flash drive with some code from years ago. They swear it contains some useful snippets that will improve your aligner, but it's in a language you haven't worked with before. You inspect the code, and don't believe it contains protected data. The algorithm was published many years ago in a leading journal. Is it okay to ask AI what the code is doing?

