# VIDEO Introduction to Understanding Unfamiliar Code with AI

This video discusses how AI can be useful when understanding code written by someone else.

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/DIlpCC4yUtw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

You can view and download the Google Slides [here](https://docs.google.com/presentation/d/1gYxHub8Vuf8uY8xI65R5HL0R31rETtxkQDLiBgb820U/edit#slide=id.g29860008570_0_387).

<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22e15d27e55_4_0.png" alt="The dinosaur cartoon says in a speech bubble, 'It’s like having a paired programmer explain things to you.'." width="100%" style="display: block; margin: auto;" />

While anyone can learn to understand code written by someone else, using AI language models to achieve this has three significant advantages.

1. _Summarize large codebases._ AI can quickly scan large codebases and give you a high-level overview of what they do. This can save you a lot of time and effort, especially when dealing with complex codebases. For example, AI can identify the main functions and classes in a codebase, and it can show you how they are related.

1. _Analyze the code._ AI can look at the code and tell you about its structure, complexity, and potential defects quickly and efficiently. This can help you understand the code better and make it easier to maintain and improve. For example, AI can identify parts of the code that are difficult to understand or maintain, and it can suggest ways to improve the code.

1. _Understand comments and documentation._ AI can read comments and documentation written by other developers. This can help you understand the code's purpose and the assumptions and limitations of the codebase. For example, AI can identify the key assumptions that are made in the code, and it can explain the trade-offs that were made in the design of the code.

::: {.ethics}
Keep these ethical considerations in mind when using AI to summarize code.

**Who owns the code?** If you are not the owner of the code, you should get permission from the owner before summarizing it.

**What is the purpose of the summary?** If you are summarizing the code for educational or research purposes, it is likely ethical to do so. However, if you are summarizing the code for commercial purposes, you may need to get permission from the owner.

**Does the code contain any sensitive or personal information?** If the code contains any sensitive or personal information, you should take special care to protect that information.
::: 

# Understanding Unfamiliar Code

## Learning Objectives

- Recognize the benefits, limitations, and assumptions in using AI to understand unfamiliar code
- Consider the ethical questions around using AI to understand another person's code
- Practice using AI to summarize code, identify an unknown coding language, and interpret regex and unknown functions

## Reading Unfamiliar Code Is A Skill

As a programmer, you will frequently encounter situations where you need to read and understand code written by other developers. This could be because you are collaborating on a project, you have taken over maintenance of an existing codebase, or you are learning new syntax or skills that require reading example codes. Comprehending code written by someone else is a distinct skill from being able to write your own code, and it takes practice to become proficient at it.

Reading unfamiliar code is like exploring an unfamiliar city without a map or a guide. Just like in a new city, you may not know where to start or how to navigate the codebase. You may encounter unfamiliar syntax, functions, and libraries that you have never seen before, just as you might encounter new streets, buildings, and landmarks. At first, you may feel disoriented and overwhelmed, and may need to spend some time getting oriented and familiarizing yourself with the environment. As you explore, you may start to see patterns and similarities, just as you might begin to recognize neighborhoods and landmarks in a new city. You may also encounter dead-ends, confusing intersections, and unexpected detours, just as you might encounter bugs and errors in the code.


<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g23a4b1a5015_0_7.png" alt="The dinosaur cartoon is holding a map while looking at a forest and says in a speech bubble, 'Where am I?'." width="100%" style="display: block; margin: auto;" />

To make progress in this unfamiliar territory, you may need to rely on a combination of intuition, deduction, and experimentation. You may need to break down the code into smaller pieces, analyze the behavior of each piece, and gradually build up a mental model of how the code works. You may also need to consult documentation, online resources, or other experts who are familiar with the codebase, just as you might ask locals or consult a map in a new city.

In the end, with patience, persistence, and a willingness to learn, you can successfully navigate the unfamiliar code and achieve your goals, just as you can successfully explore a new city and discover its hidden treasures. Learning how to read and understand code written by someone else is a valuable skill that can help you be a more effective programmer. By being able to read and comprehend unfamiliar code, you can contribute to projects more quickly, diagnose and fix bugs more effectively, and learn new programming techniques and best practices. As with any skill, the more you practice reading and understanding code written by others, the more comfortable and proficient you will become at it.


::: warning
The information presented in this course is meant for use with open source code and software. It is unclear what happens to the information fed to AI chatbots as prompts, or how secure the data are. We know data are saved and may be used to further train the AI tools, but the specifics of how data are saved, as well as how sensitive or personally identifiable information are protected, is unknown.

Err on the side of caution when interacting with them. We do **not** recommend using proprietary code or private information for prompts unless you are working with an AI that you or your company built and you know is secure.
:::

## Example One: Summarizing Code You Didn't Write

Here's some simple code using the R programming language, written by an unnamed programmer. If you are familiar with R, you might be able to understand what this code does with little effort. However, if you don't know R, you're relatively new to R, or you're just having a bad day, understanding what this bit of code can take a great deal more energy and time. AI language bots can ease that burden.

```
library(tidyverse)

d <- ggplot2::diamonds

d_sel <- d %>%
  select(carat, cut, color, clarity, depth, table, price)

d_fil <- d_sel %>%
  filter(price > 5000)

d_bin <- d_fil %>%
  mutate(carat_bins = cut_width(carat, width = 0.2))

d_summ <- d_bin %>%
  group_by(carat_bins, cut, color, clarity) %>%
  summarize(mean_price = mean(price), sd_price = sd(price))
```

We first ask [Claude-instant](https://poe.com/Claude-instant) (as implemented by Poe) to explain the purpose of this code.

:::{.query}
What does this code do?
:::

<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22de39942ac_22_0.png" alt="The output from Claude explains the code imports the diamond dataset, then manipulates and filters the data." width="100%" style="display: block; margin: auto;" />



You can ask for Claude to summarize each step in detail as well.

:::{.query}
Can you explain what each step does in detail?
:::

<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22e0106807c_0_5.png" alt="The output from Claude explains what each step of the code does. First it loads the tidyverse collection of packages, then imports the diamonds dataset from ggplot2. After that, it selects columns from diamonds: carat, cut, color, clarity, depth, table and price and stores the result in d_sel, then filters d_sel to only keep rows where price is greater than 5000 and stores the result in d_fil. Next it uses mutate() to create a new column carat_bins which bins the carat column into 0.2 width bins and stores the result in d_bin, then uses group_by() to group d_bin by carat_bins, cut, color and clarity. Finally it uses summarize() to calculate the mean and standard deviation of price for each group and stores the result in d_summ." width="100%" style="display: block; margin: auto;" />



Maybe you've never worked with the tidyverse package in R - Claude can tell you about it.

:::{.query}
What is the tidyverse package?
:::

<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22e0106807c_0_14.png" alt="The output from Claude explains that the tidyverse  is a collection of R packages useful for data wrangling, visualization, transformation, modeling, and workflow management." width="100%" style="display: block; margin: auto;" />



You might also not be familiar with the diamonds dataset (especially if you've never used it before) and want some clarification on where the data are from.

:::{.query}
Can you tell me more about the diamonds dataset?
:::

<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22e0106807c_0_20.png" alt="Claude explains the diamonds dataset is a famous R dataset that is built-in to the ggplot2 package and contains information on 50,000 diamonds and their prices. Each diamond had 539 different attributes." width="100%" style="display: block; margin: auto;" />



## Example Two: Identifying a Coding Language

Sometimes you might have to work with legacy code. Legacy code can be difficult to work with, especially if it is written in a language or style with which you are not familiar. There are more than 700 programming languages in use today, so it is impossible for any programmer to know them all. AI can be a helpful tool for identifying the language and version of legacy code, which can make your life just a little easier.

Let's look at example code that might have been written decades ago.

```
program temperature_smog_analysis;

uses
  Math;

const
  n_temperatures = 1000;
  n_smog_measures = 500;

type
  TemperatureArray = array[0..n_temperatures-1] of integer;
  SmogArray = array[0..n_smog_measures-1] of integer;

var
  temperatures: TemperatureArray;
  smog_measures: SmogArray;
  combined_data: array of integer;
  slope, y_intercept: double;
  i, j: integer;

function connect_to_database(filename: string): integer;
begin
  { implementation of connect_to_database function }
end;

function retrieve_temperatures(fd: integer): integer;
begin
  { implementation of retrieve_temperatures function }
end;

function retrieve_smog_measures(fd: integer): integer;
begin
  { implementation of retrieve_smog_measures function }
end;

function retrieve_temperature(fd, index: integer): integer;
begin
  { implementation of retrieve_temperature function }
end;

function retrieve_smog_measure(fd, index: integer): integer;
begin
  { implementation of retrieve_smog_measure function }
end;

procedure close_database(fd: integer);
begin
  { implementation of close_database function }
end;
```

We can ask [Bard](https://bard.google.com/) to take a guess at what the coding language might be.

:::{.query}
What language is this code written in?
:::

<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22e0106807c_0_46.png" alt="According to Bard, this code was written in Pascal, a procedural programming language named after French mathematician Blaise Pascal." width="100%" style="display: block; margin: auto;" />



We can explore further to figure out what indicators tell Bard the language is Pascal.

:::{.query}
How do you know this is Pascal?
:::

<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22e0106807c_0_50.png" alt="Bard explains that many of the keywords and clauses are common to Pascal syntax." width="100%" style="display: block; margin: auto;" />



It turns out there are multiple versions of Pascal. Since you will presumably need to work with this legacy code, you might want to know which version it is.

:::{.query}
What version of Pascal is this?
:::

<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22e0106807c_0_39.png" alt="Bard explains the code uses Turbo Pascal 7.0 syntax, based on the 'uses' clause, the 'Math' unit, and the 'writeln' function. These features were introduced in Turbo Pascal 7.0" width="100%" style="display: block; margin: auto;" />



## Example Three: Interpreting Regex

Regex (short for Regular Expressions) is a sequence of characters that define a search pattern. Regular expressions can be a powerful tool for data cleaning, text mining, and data validation. They are widely used in web development, data science, and other fields where text processing is important. They can also be tricky to understand at first because they involve a specific syntax that can be complex.

We can use [ChatGPT](https://chat.openai.com/) to explain regex in a bit of someone else's code.

```
x = sub("/d/e","/d",x)
```

:::{.query}
What does this do?
:::

<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22de39942ac_6_4.png" alt="ChatGPT explains this code replaces the substring /d/e with the substring /d." width="100%" style="display: block; margin: auto;" />



## Example Four: Demystifying Functions

Sometimes we get handed code that includes complex architecture. Perhaps you are working with code you wrote years ago when you really liked loops, but present you finds them difficult to parse. (Be nice to past you - maybe you were a baby programmer and didn't know better.) Instead of giving yourself a headache, you could turn to [ChatGPT](https://chat.openai.com/) to explain what your old code does.


``` python
def my_function(x):
    result = x
    for i in range(10):
        for j in range(5):
            result = result + 2 * (i + 1) * (j + 1) * (i % 2 == 0 and j % 2 == 0) - 1
    return result
```

:::{.query}
What does this function do?
:::

<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22e0106807c_0_170.png" alt="ChatGPT explains the math operations being done on variable x by this complex looped function." width="100%" style="display: block; margin: auto;" />


Well, now you have an idea what past-you might have been attempting to do with this code. You can also query AI about the potential problems from using the code as-written.

:::{.query}
What are some possible issues with this code?
:::

<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22e0106807c_0_176.png" alt="ChatGPT identifies four possible issues in the way the function was written: readability, efficiency, how the variables are named, and the use of numbers instead of variables within the function." width="100%" style="display: block; margin: auto;" />



(And if you do ever run across an expression like this in your code, you can check out our chapter on [refactoring code](https://hutchdatascience.org/AI_for_Efficient_Programming/refactoring-code.html#refactoring-code) using AI to fix it!)

## Limitations 

Although chatbots can be extremely helpful for better understanding someone else's code, if there is a lack of annotation or documentation, it will be difficult to discern more about the context of the development.

Cases where developers may not have provided context information include:

1) Not stating their purpose for writing this code.
2) Not describing what they planned to do next.
3) Not describing (or being aware of) possible parts of the code that need updating or maybe have security or privacy issues.
4) Not describing how they made certain decisions in the development process.

Although we can't truly understand some of this information, it is however possible to get some assistance from chatbots with prompts such as:

1) What do you think the purpose of this code is?
2) What might be possible next steps to further develop this code?
3) What are possible issues with this code, particularly for security or privacy?
4) Why was the code possibly written with this structure? What other options are possible?

Chatbot tools are also limited in terms of how up-to-date their training data is to know about current possible issues with code. 


# VIDEO Understanding Unfamiliar Code Main Points

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/6Mxtp2kOjV0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

* Understanding code written by someone else can be made easier by using AI
* AI chatbots can summarize the code and the dataset used, as well as clarify functions and expressions that are confusing
* AI chatbots can also identify the coding language and version used in legacy code
* Be mindful of who owns the code and what the summary will be used for when using AI to summarize someone else's code

You can view and download the Google Slides [here](https://docs.google.com/presentation/d/1ygsb4nNLEsHugrXqbeiWUm9IrfvK4Y4f8teZlQAMWNM/edit#slide=id.g29848e7ae84_1_188).
