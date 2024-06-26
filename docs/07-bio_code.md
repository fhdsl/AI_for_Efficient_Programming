


# (PART\*) Additional Learning {-}

# AI for Bioinformatics

## Learning Objectives

- Understand the potential applications of AI assistance in bioinformatics software development
- Identify the challenges and considerations when using AI in bioinformatics software development
- Grasp the serious ethical concerns when designing bioinformatics software that deals with sensitive data

## AI in Bioinformatics

[Bioinformatics](https://www.genome.gov/genetics-glossary/Bioinformatics) is an interdisciplinary field that combines biology, computer science, statistics, and data analysis to extract insights from biological data. It involves the development and application of computational tools, algorithms, and databases to store, organize, analyze, and interpret vast amounts of biological information, particularly in the context of genomics and public health. [Biomedical imaging](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5171495/) and [electronic health record](https://en.wikipedia.org/wiki/Electronic_health_record) informatics are also rapidly growing subdisciplines.

Bioinformatics is especially important for research and work done with genomes. In genomics, bioinformatics enables the identification and annotation of genes, the prediction of protein structures and functions, and the analysis of genetic variations, such as single nucleotide polymorphisms and gene copy number variations. These analyses help in unraveling the genetic basis of diseases, discovering potential drug targets, and facilitating personalized medicine approaches.

The proliferation of genomic data in recent years have been transformative for the field of genomics. Advances in DNA sequencing technologies, particularly next-generation sequencing, have revolutionized the ability to generate vast amounts of genomic data quickly and at a reduced cost. This has led to an unprecedented increase in the availability and accessibility of genomic information. Researchers estimate that we will generate [between 2 and 40 exabytes of genomic data](https://www.genome.gov/about-genomics/fact-sheets/Genomic-Data-Science) within the next decade. Cloud computing platforms like [AnVIL](https://anvilproject.org/) are on the forefront of addressing the big genomic data storage and processing challenge.

You have seen principles in previous chapters that likewise apply to creating bioinformatics software. Creating bioinformatics software, however, comes with its own unique sets of challenges:

<img src="resources/images/07-bio_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g2313f95cd49_180_4.png" alt="Bioinformatics dino is excited to get started. It is wearing a lab coat and gloves and is saying 'Don’t worry - We can use bioinformatics to fill in the blanks with frog DNA!'." width="100%" style="display: block; margin: auto;" />

- **Data Complexity**: Genomic data is vast and complex, often consisting of large datasets with multiple dimensions, such as nucleotide sequences and quality scores, gene expression levels, and epigenetic modifications. Developing algorithms and software tools to efficiently handle and analyze this data requires expertise in data management, processing, and interpretation as well as the biological domain knowledge.

- **Diverse Data Types**: Bioinformatics software often handles diverse and complex data outside of strings and numeric types, such as [Bioconductor's `Single Cell Experiment`](https://www.bioconductor.org/packages/release/bioc/vignettes/SingleCellExperiment/inst/doc/intro.html) data class. Knowledge of common data types used in bioinformatics is required to create functional software.

- **Algorithmic Complexity**: Developing accurate and efficient algorithms for various bioinformatics tasks, such as sequence alignment, gene prediction, and protein structure prediction, requires deep understanding of biological principles and computational techniques. Designing algorithms that can handle noise, errors, and biological variations is a persistent challenge.

- **Integration with Existing Workflows**: Bioinformatics software is often part of a larger analysis pipeline or workflow. Integrating AI-based tools seamlessly into existing bioinformatics pipelines and workflows, ensuring compatibility, and maintaining data integrity throughout the process requires special attention.

- **Ethical Considerations**: People are typically more sensitive about their health data when compared to their Amazon purchases. This is for a good reason: there is a painful history of the medical establishment performing experiments on people with less socio-political power. Like medical record data, genomic data is supposed to be [carefully protected](https://www.genome.gov/about-genomics/policy-issues/Privacy) so that it can't be used to disadvantage certain individuals. AI tools on the other hand, are not typically designed with security and data sovereignty in mind.

## Using these topics for Bioinformatics

When using AI to help generate code examples, perform refactoring, understand code, or create unit tests, you should keep the following in mind:

- [**Writing Code**](writing-code.html): AI can be used to automatically generate bioinformatics code snippets or functions. It can provide code suggestions, auto-completion, or even generate code based on given specifications or data classes. This can include creating some [unit tests](https://en.wikipedia.org/wiki/Unit_testing) for your functions to ensure they are working as expected.

- [**Refactoring Code**](refactoring-code.html): AI can aid in refactoring bioinformatics code to improve readability, maintainability, and performance through suggestions for code restructuring.

- [**Annotating Code**](annotating-your-code.html): Bioinformatics tools can be used for clinical decision making. It's important that anyone vetting or auditing your tool can trace any decision making steps. Therefore, clear understanding and documentation are key. AI can assist in drafting documentation and code annotations, such as through summarizing code functionality, clarifying complex expressions or functions, and/or providing plain-terms explanations of the underlying algorithms.

- [**Understanding Code**](understanding-unfamiliar-code.html): Although bioinformatics is rapidly evolving, its often specific use cases mean that sometimes developers have to work with code that is quite old or outdated. AI can help identify the coding language and version used in legacy bioinformatics code. This can be valuable when working with older software or when integrating different codebases.

:::{.warning}
**NEVER** submit chunks of code to AI tools without being 100% sure that they are free from [personally identifiable information (PII)](https://toolkit.ncats.nih.gov/glossary/personally-identifiable-information/). PII includes variables like gender, race, birth date, geographic location, and disease diagnosis. If you need to, generate dummy data to test your code.
:::


# VIDEO AI for Bioinformatics Main Points

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/P5_sZlQKTEE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


- Like other types of software, bioinformatics software and tools can benefit from AI assistance for writing, refactoring, annotating, and understanding code.
- Biological data and workflows can be complex. AI does not replace a thorough understanding of biological processes at play.
- **NEVER** submit any protected or sensitive data to AI applications. This can constitute a serious, often illegal breach of subject privacy if you are dealing with data from people.

You can view and download the Google Slides [here](https://docs.google.com/presentation/d/1bvd0X57ukyS6l2uffQscXRBHxWc8y9-UZFZe39BETDs/edit#slide=id.g2983f25f381_0_188).



