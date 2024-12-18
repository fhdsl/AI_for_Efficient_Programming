# VIDEO Introduction to Annotating Code with AI

This video discusses why AI is a good tool to help with code annotation.

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/XuHVtnED2zQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

You can view and download the Google Slides [here](https://docs.google.com/presentation/d/1ufNeULKBS4gMd7KQECsfFVxlRefWVs2pvjwRc5r8EBA/edit#slide=id.p).

We've discussed why code annotation and documentation are important, but when and why would you use AI for code annotation? AI can be a nice tool to supplement the annotation of your code. It should not be the only source of annotation for your code, because as the code author, you need to verify that what AI has annotated is consistent with your knowledge and history of development of the code.

But using AI to annotate your code can be useful to supplement existing code annotations or to annotate old code that was poorly annotated either by yourself or others who are no longer working on the project.

Here are some of the benefits of using AI for code annotation:

1. **Speed and efficiency:** AI algorithms can analyze code much faster than humans, which means they can quickly generate comments and annotations for large codebases. This can save developers significant time and effort, allowing them to focus on other aspects of the development process.

1. **Consistency:** Unlike humans, AI is not affected by personal biases or preferences, so it can provide consistent annotations across different code files and projects. A human may underestimate places in the code that should have annotation, whereas an AI might be more consistent at putting annotation in these places. This can help ensure that all code in a project is well-documented and easy to understand.

1. **Objectivity:** AI can analyze code objectively and identify potential issues that may have been missed by humans. This can lead to better quality code that is easier to maintain and less prone to errors.

1. **Learning:** AI models can learn from large datasets of annotated code and improve their ability to generate comments and annotations over time. This means that the more code the AI model analyzes, the more accurate and effective it becomes at annotating code.

1. **Specificity:** AI models can be trained on specific programming languages, frameworks, or libraries, allowing them to generate language-specific comments and annotations that are tailored to the needs of the project. This can be particularly helpful for large, complex projects that require specialized knowledge or expertise.

## Ethics of using AI to annotate code

However, there are also a number of potential ethical concerns associated with using AI to annotate code. For example, we don't yet know how and in what ways AI models may be biased. Additionally, AI models may be opaque, which could make it difficult to understand why they made certain annotations. Finally, because AI models are not humans and don't necessarily tell the stories behind the code, they may be used to generate annotations that are not accurate, helpful, or do not tell the full depth of the history of what occurred with the code, which could lead to problems.

Given these potential benefits and concerns, it is important for users of AI to always realize that they are ultimately accountable for the annotation that an AI model makes, and careful review of this annotation is needed.

There are a number of ethical considerations to take into account when using AI to annotate code. Here are a few of the most important considerations:

1. **Accountability:** First and foremost, a user of AI is always primarily accountable for any output that they use from an AI model. AI models can give you annotation to start with, but it is up to you as the user to verify and review this output carefully. The user of the AI model is ultimately responsible for keeping or throwing out the annotations the AI makes and thus is responsible for using errors that the model makes. Much like a user of a Google Search engine is responsible for which results they use, a user of AI is responsible what output from the AI model they use.

2. **Transparency:** It is important to be transparent about the use of AI in code annotation. This means disclosing the fact that AI is being used, as well as the specific AI model and dataset that is being used. This should be stated on every file where annotation has been made using AI. This transparency allows others who view the code to be able more fully interpret the AI-created annotation that accompanies the code.

3. **Bias:** AI models are trained on data, and this data can introduce bias into the model. It is important to be aware of the potential for bias and to take steps to mitigate it. This can be done by using a diverse dataset, by carefully selecting the features that are used to train the model, and by using techniques such as adversarial training. It is important to provide annotations that indicate any known biases, possible limitations associated with bias, and any strategies that were used to mitigate bias.

4. **Explainability:** It is important to be able to explain the decisions that an AI model makes. This is especially important in the case of code annotation, where the decisions made by the AI model can have a significant impact on the quality of the code. There are a number of techniques that can be used to explain the decisions of an AI model, such as visualization and rule extraction. You can (and should) ask a chatbot to explain its sources and rationale for output that it gave. (Be aware that actual citations it gives may or may not be accurate, and you need to verify the accuracy of those citations by doing your own follow up literature search).

# Annotating Your Code

## Learning Objectives

- Explain the significance and benefits of code annotation and how it aids in understanding and working with code in the future.
- Demonstrate the ability to apply effective code annotation practices by providing clear and concise comments in code. 
- Recognize the impact of code annotation on code maintainability.
- Explain how well-annotated code can facilitate collaboration among developers and ensure code consistency.
- Critically evaluate the use of AI in code annotation, including benefits, ethical considerations, and limitations.
- Explore how AI can be used to create README files, do line-by-line annotations, and offer potential code improvements.

## Annotating Code is Good Practice

Code annotation, also known as code commenting, is the process of adding explanatory notes to source code. These notes are used to provide context, clarify functionality, and aid in understanding for developers who may be working on the codebase in the future. Code annotation is an important practice for any developer looking to write clear, efficient, and maintainable code.

There are many benefits to annotating code:

- Improves readability
- Improves maintainability
- Improves quality

::: warning
The information presented in this course is meant for use with open source code and software. It is unclear what happens to the information fed to AI chatbots as prompts, or how secure the data are. We know data are saved and may be used to further train the AI tools, but the specifics of how data are saved, as well as how sensitive or personally identifiable information are protected, is unknown.

Err on the side of caution when interacting with them. We do **not** recommend using proprietary code or private information for prompts unless you are working with an AI that you or your company built and you know is secure.
:::

## Improves readability

<img src="05-annotation_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22de39942ac_19_8.png" alt="Dino says It’s great this code is well annotated using AI. I totally forgot what I was doing with this code when I wrote it. " width="100%" style="display: block; margin: auto;" />

First, it can help to improve the readability of code. By adding comments, developers can explain the purpose of each section of code, which can make it easier for others to understand what the code is doing. This can be especially helpful for large or complex codebases, where it can be difficult to keep track of all the different components. This is particularly important in contexts where the original developer of a project may move on to something else and others are left to work on them. Annotation perhaps most often helps a developer remember things they knew about the code when they were originally writing it (annotation is helpful for future you!) If the original developer left well-annotated code, it can drastically improve the ability of others (and their future selves) to continue with the project.

### Examples of readability aiding comments

Comments that help readability **clarify what the code is doing**

**Function explanations:**  A comment at the beginning of a function or method can describe its purpose, parameters, and expected return values. This makes it easier for others to understand what the function does and how to use it.

```
# This function calculates and returns the sum of two numbers (x and y)
def add_numbers(x, y):
    return x + y
```

**Inline explanations:** Use inline comments to explain what a specific line or block of code does. This can help someone reading your code to quickly understand what's going on.
```
# Loop through each item in the list
for item in my_list:
    # Check if the item is greater than 10
    if item > 10:
        # Print the item
        print(item)
```

**TODO comments:** Use TODO comments to mark areas of your code that need further work or improvement. This can help you or others to remember to come back to a specific part of the code.

```
# TODO: Implement error handling for this function
def my_function():
    pass
```

**Parameter descriptions:** If a function or method has complex parameters, it can be helpful to add comments explaining what each parameter does.

```
def my_function(parameter1, parameter2):
    """
    Calculate the sum of two numbers.

    Parameters:
    parameter1 (int): The first number to be added.
    parameter2 (int): The second number to be added.

    Returns:
    int: The sum of parameter1 and parameter2.
    """
    return parameter1 + parameter2
```

**Code block summary explanations:**  If you have a long or complex code block, you can add a comment to explain what the block is doing.

```
# This code block creates a dictionary containing the counts of each word in a list of text strings
word_counts = {}
for text in text_list:
    for word in text.split():
        if word not in word_counts:
            word_counts[word] = 0
        word_counts[word] += 1
```

## Improves maintainability

<img src="05-annotation_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22de39942ac_19_37.png" alt="The Dinos say ‘It’s easier for us to both work to maintain this code since it is so well annotated!’" width="100%" style="display: block; margin: auto;" />

Code annotation can help to improve the maintainability of code. By adding comments, developers can explain the reasoning behind certain decisions, which can make it easier for others to make changes to the code without breaking it. This can be especially helpful when multiple developers are working on the same codebase, as it can help to prevent conflicts and ensure that the code is always in a consistent state.

### Examples of maintainability aiding comments

Comments that help maintainability **explain the historical context of why code was made the way it was**

**Examples of maintainability aiding comments**

**Design decisions:** If there were specific design decisions made when creating the code, you can add comments explaining why certain choices were made.
bash

```
# We chose to use a linked list data structure for this function to reduce the time complexity of inserting and deleting elements.
```

**Legacy code:** Sometimes, code may have been written in a certain way due to constraints or limitations at the time it was created. Adding comments to explain this can help others understand why the code is the way it is.

```
# This code was written before Python 3, which introduced the `yield from` syntax. Therefore, we used a `for` loop to iterate over the nested list.
```

**Performance optimizations:** If certain performance optimizations were made to the code, you can add comments explaining why they were necessary.
bash

```
# We used memoization to improve the time complexity of this recursive function, as it was taking too long to execute for larger inputs.
```

**Compatibility considerations:** If the code was written with compatibility considerations in mind, you can add comments explaining why certain choices were made.

```
# We used the `os.path` module to ensure that this code will work on both Windows and Unix-based systems, as the path separators are different on each platform.
```

**Limitations:** If there are limitations or edge cases that the code cannot handle, you can add comments to explain this to others.

```
# Note that this function assumes that the input array is sorted in ascending order. If the array is unsorted, the results may be incorrect.
```

## Improves the quality

<img src="05-annotation_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22de39942ac_19_60.png" alt="Dino says Ah I know exactly how to fix this part of the code that was annotated with a warning!" width="100%" style="display: block; margin: auto;" />

Code annotation can help to improve the quality of code. By adding comments, developers can identify potential issues or edge cases, which can help to prevent these issues from occurring in the first place. This can be especially helpful when testing code, as it can help to ensure that the code is working as expected.

## Examples of quality aiding comments

Comments that help improve the quality of the code **by explaining to others how to use it or help improve it**

**Error handling:** Adding comments to explain how and why error handling is being implemented can help ensure that your code is robust and able to handle unexpected inputs or errors. This helps others know how the code was intended to be used.

```
# If the input argument is not a list or is empty, raise a ValueError
if not isinstance(input_list, list) or len(input_list) == 0:
    raise ValueError("Input must be a list that is not empty")
```

**Complexity:** If your code has particular complexities, adding comments that explain it can help others understand the performance characteristics of your code. It may help others identify whether there is a simpler way to write the code. By adding a comment that expresses uncertainty about the code and asking for suggestions, the author can potentially receive feedback from others on how to improve the code.

```
# This block of code could probably be simplified, but I'm not sure how.
new_list = []
for i in old_list:
    if i > 0:
        new_list.append(i)
```

**Constants and variables:** Adding comments to explain the purpose of constants and variables can make your code easier to use. It not only notifies others of the variables existence but lets them know if they need to change the parameters for their own purposes.

```
# This constant represents the maximum allowed number of retries when attempting to connect to the server.
MAX_RETRIES = 3

# This variable tracks the number of failed attempts to connect to the server.
num_retries = 0
```

**Code organization or disorganization:** Adding comments to explain the organization and structure of your code can make it easier for others to navigate and may bring out a better organizational strategy for your code.

```
# Define helper functions for data processing
def preprocess_data(input_data):
    # Implementation details

def analyze_data(processed_data):
    # Implementation details

def visualize_data(analyzed_data):
    # Implementation details

# Load data from file
input_data = load_data("input.txt")

# Preprocess data
processed_data = preprocess_data(input_data)

# Analyze data
analyzed_data = analyze_data(processed_data)

# Visualize data
visualize_data(analyzed_data)
```

**Assumptions and constraints:** Adding comments to explain the assumptions and constraints of your code can help others understand its limitations and potential pitfalls.

```
# This function assumes that all input values are positive integers. Negative or non-integer inputs may result in unexpected behavior.
```

## Examples on using AI for annotation

### Ask for a README summary

To try out some annotation with code examples, this author dug up some old code that she had no idea about what it did anymore because time had passed and she didn't document it very well.

First, I wanted ChatGPT to make a README for me. README's are a standard file that explain what the code base does and provides a summary of what is happening in the set. I asked ChatGPT if it could:

:::{.query}
Create a README for this code
:::

and then I pasted the old code.

<img src="05-annotation_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22de39942ac_19_60.png" alt="The author asked ChatGPT to create a README for some old code." width="100%" style="display: block; margin: auto;" />

ChatGPT gave me some output that generally looked like a README:

<img src="05-annotation_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22de39942ac_19_96.png" alt="ChatGPT provided a README. It is titled README for code snippet." width="100%" style="display: block; margin: auto;" />

This README seems accurate given the work I was doing at the time. But obviously the title isn't great -- it doesn't describe the code well. Plus there's not really information about usage or outputs of the code.

So I asked it:

:::{.query}
Can you make this README more succinct and with sections about how you would use this code?
:::

This yielded a much better result.

<img src="05-annotation_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22de39942ac_19_101.png" alt="ChatGPT provided a better README after I asked it to be more succinct and provide sections about how to use the code. " width="100%" style="display: block; margin: auto;" />

### Ask for line by line annotation

Second, I wanted to have ChatGPT annotate code line by line. So I asked it

:::{.query}
Can you annotate some R code for me?
:::

<img src="05-annotation_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22de39942ac_19_87.png" alt="I asked ChatGPT to annotate old R code." width="100%" style="display: block; margin: auto;" />
It not only provided helpful annotations but it fixed spacing and added more spaces between lines of code:

<img src="05-annotation_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22de39942ac_19_91.png" alt="ChatGPT provided annotations for the code I provided." width="100%" style="display: block; margin: auto;" />

It does however, think the code is Python apparently if we look in the upper left corner.
But this doesn't seem to have affected its accuracy in its annotations.

### Ask for how the code could be improved

This code is old, and I don't think it runs properly and is in no way reproducible. So I wanted to see what ChatGPT would recommend for improvements to the code. I said

:::{.query}
How could I make this code better?
:::

It had a lot of great advice:

<img src="05-annotation_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22de39942ac_19_79.png" alt="ChatGPT offered ways to improve my old code." width="100%" style="display: block; margin: auto;" />

First and foremost it told me my variable names are not consistent and also not descriptive. Which is completely accurate! There's variable names like `xx` and `ll` which don't tell the reader anything about the variable.

### Style the code

Next, I asked chatGPT if it could restyle the code into tidyverse style. It definitely put elements that look like tidyverse however, it also put items in the code that I can tell by looking at it won't work.  

So I tried to tell it about the errors:
:::{.query}
This code is close but there are some errors. These tidyverse functions don't work with matrices.
:::

and it told me:

```
You are correct that the tidyverse functions are designed to work with data frames and not matrices. Here's a modified version of your code that converts the matrix to a data frame and uses tidyverse functions:
```

The lesson here is that the output of chatGPT still needs to be vetted by the person asking for it. It is a great idea to continue to have AIs work on something if it isn't quite what you are asking for, however, at the end of the day it is you, the human, who has to vet the output.

### Sometimes it has trouble with file types if given a URL

Copying and pasting code appears to be the best way to go at this point in time.

I asked chatGPT if it could annotate code in a Jupyter notebook at a URL I gave it:

:::{.query}
Can you annotate the code at this URL? https://github.com/jhudsl/reproducible-python-example/blob/main/make_heatmap.ipynb
:::

It responded with some of the code at that file where it was annotated but most of the notebook was not there.

I told ChatGPT:

:::{.query}
That isn't all the code at that url
:::

ChatGPT told me:

```
You're right, I apologize. The code at the given URL is actually in a Jupyter Notebook format, so it's not easy to copy-paste here. However, I can suggest an alternative approach: you can use the website nbviewer (https://nbviewer.jupyter.org/) to view the notebook and its code. Here are the steps to do so:

Go to https://nbviewer.jupyter.org/

Paste the URL of the notebook https://github.com/jhudsl/reproducible-python-example/blob/main/make_heatmap.ipynb into the "Enter the location of a Jupyter Notebook" field and press "Go".

This will display the notebook and its code, and you can read through it and add your own annotations as needed.
I hope this helps!
```

This was a nice tool to recommend, however it still told me I should add my own annotations at the end of this.

# VIDEO Annotating Your Code Main Points

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/oX61I1NDOFI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


- Code annotation is important for readability, maintainability, and overall quality of code
- AI can be a helpful tool for supplementing annotations or creating annotation for poorly annotated code.
- Ultimately the code author who uses AI as a tool for annotation is still responsible for verifying that the annotations are consistent with their knowledge of the code.

You can view and download the Google Slides [here](https://docs.google.com/presentation/d/10_hzwnNx11xafpmHbV6H9XJ4BHPAjMzFvgxlAnrD5hY/edit#slide=id.g29847d27b96_0_188).





``` r
devtools::session_info()
```

```
## ─ Session info ───────────────────────────────────────────────────────────────
##  setting  value
##  version  R version 4.3.2 (2023-10-31)
##  os       Ubuntu 22.04.4 LTS
##  system   x86_64, linux-gnu
##  ui       X11
##  language (EN)
##  collate  en_US.UTF-8
##  ctype    en_US.UTF-8
##  tz       Etc/UTC
##  date     2024-12-18
##  pandoc   3.1.1 @ /usr/local/bin/ (via rmarkdown)
## 
## ─ Packages ───────────────────────────────────────────────────────────────────
##  package     * version date (UTC) lib source
##  askpass       1.2.0   2023-09-03 [1] RSPM (R 4.3.0)
##  bookdown      0.41    2024-10-16 [1] CRAN (R 4.3.2)
##  bslib         0.6.1   2023-11-28 [1] RSPM (R 4.3.0)
##  cachem        1.0.8   2023-05-01 [1] RSPM (R 4.3.0)
##  chromote      0.3.1   2024-08-30 [1] CRAN (R 4.3.2)
##  cli           3.6.2   2023-12-11 [1] RSPM (R 4.3.0)
##  curl          5.2.0   2023-12-08 [1] RSPM (R 4.3.0)
##  devtools      2.4.5   2022-10-11 [1] RSPM (R 4.3.0)
##  digest        0.6.34  2024-01-11 [1] RSPM (R 4.3.0)
##  dplyr         1.1.4   2023-11-17 [1] RSPM (R 4.3.0)
##  ellipsis      0.3.2   2021-04-29 [1] RSPM (R 4.3.0)
##  evaluate      0.23    2023-11-01 [1] RSPM (R 4.3.0)
##  fansi         1.0.6   2023-12-08 [1] RSPM (R 4.3.0)
##  fastmap       1.1.1   2023-02-24 [1] RSPM (R 4.3.0)
##  fs            1.6.3   2023-07-20 [1] RSPM (R 4.3.0)
##  generics      0.1.3   2022-07-05 [1] RSPM (R 4.3.0)
##  glue          1.7.0   2024-01-09 [1] RSPM (R 4.3.0)
##  highr         0.11    2024-05-26 [1] CRAN (R 4.3.2)
##  hms           1.1.3   2023-03-21 [1] RSPM (R 4.3.0)
##  htmltools     0.5.7   2023-11-03 [1] RSPM (R 4.3.0)
##  htmlwidgets   1.6.4   2023-12-06 [1] RSPM (R 4.3.0)
##  httpuv        1.6.14  2024-01-26 [1] RSPM (R 4.3.0)
##  httr          1.4.7   2023-08-15 [1] RSPM (R 4.3.0)
##  janitor       2.2.0   2023-02-02 [1] RSPM (R 4.3.0)
##  jquerylib     0.1.4   2021-04-26 [1] RSPM (R 4.3.0)
##  jsonlite      1.8.8   2023-12-04 [1] RSPM (R 4.3.0)
##  knitr         1.48    2024-07-07 [1] CRAN (R 4.3.2)
##  later         1.3.2   2023-12-06 [1] RSPM (R 4.3.0)
##  lifecycle     1.0.4   2023-11-07 [1] RSPM (R 4.3.0)
##  lubridate     1.9.3   2023-09-27 [1] RSPM (R 4.3.0)
##  magrittr      2.0.3   2022-03-30 [1] RSPM (R 4.3.0)
##  memoise       2.0.1   2021-11-26 [1] RSPM (R 4.3.0)
##  mime          0.12    2021-09-28 [1] RSPM (R 4.3.0)
##  miniUI        0.1.1.1 2018-05-18 [1] RSPM (R 4.3.0)
##  openssl       2.1.1   2023-09-25 [1] RSPM (R 4.3.0)
##  ottrpal       1.3.0   2024-10-23 [1] Github (jhudsl/ottrpal@2e19782)
##  pillar        1.9.0   2023-03-22 [1] RSPM (R 4.3.0)
##  pkgbuild      1.4.3   2023-12-10 [1] RSPM (R 4.3.0)
##  pkgconfig     2.0.3   2019-09-22 [1] RSPM (R 4.3.0)
##  pkgload       1.3.4   2024-01-16 [1] RSPM (R 4.3.0)
##  processx      3.8.3   2023-12-10 [1] RSPM (R 4.3.0)
##  profvis       0.3.8   2023-05-02 [1] RSPM (R 4.3.0)
##  promises      1.2.1   2023-08-10 [1] RSPM (R 4.3.0)
##  ps            1.7.6   2024-01-18 [1] RSPM (R 4.3.0)
##  purrr         1.0.2   2023-08-10 [1] RSPM (R 4.3.0)
##  R6            2.5.1   2021-08-19 [1] RSPM (R 4.3.0)
##  Rcpp          1.0.12  2024-01-09 [1] RSPM (R 4.3.0)
##  readr         2.1.5   2024-01-10 [1] RSPM (R 4.3.0)
##  remotes       2.4.2.1 2023-07-18 [1] RSPM (R 4.3.0)
##  rlang         1.1.4   2024-06-04 [1] CRAN (R 4.3.2)
##  rmarkdown     2.25    2023-09-18 [1] RSPM (R 4.3.0)
##  rprojroot     2.0.4   2023-11-05 [1] CRAN (R 4.3.2)
##  sass          0.4.8   2023-12-06 [1] RSPM (R 4.3.0)
##  sessioninfo   1.2.2   2021-12-06 [1] RSPM (R 4.3.0)
##  shiny         1.8.0   2023-11-17 [1] RSPM (R 4.3.0)
##  snakecase     0.11.1  2023-08-27 [1] RSPM (R 4.3.0)
##  stringi       1.8.3   2023-12-11 [1] RSPM (R 4.3.0)
##  stringr       1.5.1   2023-11-14 [1] RSPM (R 4.3.0)
##  tibble        3.2.1   2023-03-20 [1] CRAN (R 4.3.2)
##  tidyselect    1.2.0   2022-10-10 [1] RSPM (R 4.3.0)
##  timechange    0.3.0   2024-01-18 [1] RSPM (R 4.3.0)
##  tzdb          0.4.0   2023-05-12 [1] RSPM (R 4.3.0)
##  urlchecker    1.0.1   2021-11-30 [1] RSPM (R 4.3.0)
##  usethis       2.2.3   2024-02-19 [1] RSPM (R 4.3.0)
##  utf8          1.2.4   2023-10-22 [1] RSPM (R 4.3.0)
##  vctrs         0.6.5   2023-12-01 [1] RSPM (R 4.3.0)
##  webshot2      0.1.1   2023-08-11 [1] CRAN (R 4.3.2)
##  websocket     1.4.2   2024-07-22 [1] CRAN (R 4.3.2)
##  xfun          0.48    2024-10-03 [1] CRAN (R 4.3.2)
##  xml2          1.3.6   2023-12-04 [1] RSPM (R 4.3.0)
##  xtable        1.8-4   2019-04-21 [1] RSPM (R 4.3.0)
##  yaml          2.3.8   2023-12-11 [1] RSPM (R 4.3.0)
## 
##  [1] /usr/local/lib/R/site-library
##  [2] /usr/local/lib/R/library
## 
## ──────────────────────────────────────────────────────────────────────────────
```
