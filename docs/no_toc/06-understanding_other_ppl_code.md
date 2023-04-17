# Understanding Unfamiliar Code

As a programmer, you will frequently encounter situations where you need to read and understand code written by other developers. This could be because you are collaborating on a project, you have taken over maintenance of an existing codebase, or you are learning new syntax or skills that require reading example codes. Comprehending code written by someone else is a distinct skill from being able to write your own code, and it takes practice to become proficient at it.

Reading unfamiliar code is like exploring an unfamiliar city without a map or a guide. Just like in a new city, you may not know where to start or how to navigate the codebase. You may encounter unfamiliar syntax, functions, and libraries that you have never seen before, just as you might encounter new streets, buildings, and landmarks. At first, you may feel disoriented and overwhelmed, and may need to spend some time getting oriented and familiarizing yourself with the environment. As you explore, you may start to see patterns and similarities, just as you might begin to recognize neighborhoods and landmarks in a new city. You may also encounter dead-ends, confusing intersections, and unexpected detours, just as you might encounter bugs and errors in the code.

To make progress in this unfamiliar territory, you may need to rely on a combination of intuition, deduction, and experimentation. You may need to break down the code into smaller pieces, analyze the behavior of each piece, and gradually build up a mental model of how the code works. You may also need to consult documentation, online resources, or other experts who are familiar with the codebase, just as you might ask locals or consult a map in a new city.

In the end, with patience, persistence, and a willingness to learn, you can successfully navigate the unfamiliar code and achieve your goals, just as you can successfully explore a new city and discover its hidden treasures. Learning how to read and understand code written by someone else is a valuable skill that can help you be a more effective programmer. By being able to read and comprehend unfamiliar code, you can contribute to projects more quickly, diagnose and fix bugs more effectively, and learn new programming techniques and best practices. As with any skill, the more you practice reading and understanding code written by others, the more comfortable and proficient you will become at it.

## Using AI to understand code

<img src="06-understanding_other_ppl_code_files/figure-html//1MCNeSO4aOm1iESWDLOGTcx3aLEbnu8UttV0QGVAeafE_g22e15d27e55_4_0.png" title="The dinosaur cartoon says in a speech bubble, 'It’s like having a paired programmer explain things to you.'." alt="The dinosaur cartoon says in a speech bubble, 'It’s like having a paired programmer explain things to you.'." width="100%" style="display: block; margin: auto;" />

While anyone can learn to understand code written by someone else, using AI language models to achieve this has three significant advantages. Firstly, AI tools can analyze the codebase and provide insights into its structure, complexity, and potential defects. This analysis can identify parts of the code that may be challenging to understand, maintain or improve. Based on the analysis, the AI tools may also make recommendations on how to enhance the codebase for better functionality and readability.

Secondly, AI tools can assist in summarizing large codebases, which can be challenging to comprehend in detail. Such codebases may have multiple files, functions, and classes, which could take a considerable amount of time to read and understand thoroughly. With the help of AI, programmers can get a high-level overview of the codebase without going through it line by line. This approach can save substantial time and effort, especially when dealing with complex codebases. By gaining a deeper understanding of the codebase, developers can make better-informed decisions when it comes to adding new features, improving existing functionality, or fixing bugs. AI language models can also quickly analyze large amounts of code and provide a summary of its functionality, which can save developers a significant amount of time compared to manually analyzing the code line-by-line. By automating this process, developers can devote more time to other important tasks, such as debugging, testing, and improving the code.

Finally, AI can help programmers to understand the comments and documentation written by other developers, as well as their design decisions and implementation details of code. These insights can help programmers to understand the code's purpose and the assumptions and limitations of the codebase. As a programmer, at some point you will almost certainly need to deal with "legacy code," or code written by someone else years (or decades) earlier. Often when you run across this code, the original programmer is not available to answer questions. Even if they are, they likely won't remember all the details you need about the decisions they made while creating the program. AI bots are an extremely powerful tool that can fill in the gaps of understanding, especially when the code isn't annotated well or at all. This can be especially helpful when working with older or legacy code, or when collaborating with other developers on a project. For instance, understanding how a particular piece of code works and why it was implemented a certain way can help developers identify potential issues and find more effective solutions. 

::: {.ethics}

**Ethical Considerations**

AI language models like ChatGPT, Bard, and others have the ability to summarize code and offer valuable insights into its workings. However, it's important to consider the ethics of using AI to summarize code that someone else has written. Several factors come into play, such as the intended purpose of the summary, the ownership of the code, and the potential impact of the summary. Specifically, it's important to take into account who owns the code, the reason for summarizing the code, and whether the code contains any sensitive or personal information.

If the reason for summarizing the code is for educational or research purposes, and the code is either publicly available or the owner has granted explicit permission for its use, then it's likely ethical to use AI to summarize the code. However, if the summary is intended for commercial purposes or could potentially infringe upon the owner's intellectual property rights, it may be unethical to use AI to summarize the code without obtaining the owner's consent. Additionally, if the code contains confidential or personal information, using AI to summarize it could raise privacy concerns. In such cases, obtaining explicit consent from the owner and implementing appropriate measures to ensure that the summary does not reveal any confidential information may be necessary.

Overall, the ethics of using AI to summarize code someone else wrote depend on the specific circumstances and should be carefully considered before proceeding. It is important to respect the intellectual property rights and privacy of the owner and ensure that the summary is used in a responsible and ethical manner.

::: 

## Example One: Summarizing Code You Didn't Write

Here's some simple code using the R programming language, written by an unnamed programmer. If you are familiar with R, you might be able to understand what this code does with little effort. However, if you don't know R, you're relatively new to R, or you're just having a bad day, understanding what this bit of code can take a great deal more energy and time. AI language bots can ease that burden.

```
library(tidyverse)

d <- ggplot2::diamonds

d_sel <- d %>%
  select(carat, cut, color, clarity, depth, table, price)

d_fil <- d_s %>%
  filter(price > 5000)

d_bin <- d_fil %>%
  mutate(carat_bins = cut_width(carat, width = 0.2))

d_summ <- d_bin %>%
  group_by(carat_bins, cut, color, clarity) %>%
  summarize(mean_price = mean(price), sd_price = sd(price))

ggplot(d_sum, aes(x = mean_price, y = sd_price)) +
  geom_point() +
  facet_grid(cut ~ color + clarity) +
  labs(x = "Mean Price", y = "Standard Deviation of Price")
```

We first ask [Claude-instant](https://poe.com/Claude-instant) (as implemented by Poe) to explain the purpose of this code.

:::{.query}
"What does this code do?"
:::


You can always ask for clarification if you need more information.


:::{.query}
"Can you explain what each step does in detail?"
:::

You can also ask about both the tidyverse package and the dataset being used.

:::{.query}
"What is do the tidyverse packages do?"
:::

:::{.query}
"Can you tell me more about the diamonds dataset?"
:::


## Example Two: Identifying a Coding Language

Sometimes you might have to work with legacy code. Legacy code can be difficult to work with, especially if it is written in a language or style that you are not familiar with. There are more than 700 programming languages in use today, so it is impossible for any programmer to know them all. AI can be a helpful tool for identifying the language and version of legacy code, which can make your life just a little easier.

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

begin
  SetLength(combined_data, n_temperatures + n_smog_measures);

  fd := connect_to_database('seattle_temperature.db');
  n_temperatures := retrieve_temperatures(fd);

  sfd := connect_to_database('seattle_smog.db');
  n_smog_measures := retrieve_smog_measures(sfd);

  for i := 0 to n_temperatures-1 do
  begin
    temperatures[i] := retrieve_temperature(fd, i);
    combined_data[i] := temperatures[i];
  end;

  for j := 0 to n_smog_measures-1 do
  begin
    smog_measures[j] := retrieve_smog_measure(sfd, j);
    combined_data[j + n_temperatures] := smog_measures[j];
  end;

  close_database(fd);
  close_database(sfd);

  slope := 0.0;
  y_intercept := 0.0;

  for i := 0 to n_temperatures+n_smog_measures-1 do
  begin
    slope := slope + (combined_data[i + n_temperatures] - y_intercept) *
            (combined_data[i] - y_intercept);
    y_intercept := y_intercept + (combined_data[i + n_temperatures] - y_intercept);
  end;

  slope := slope / (n_temperatures + n_smog_measures);
  y_intercept := y_intercept / (n_temperatures + n_smog_measures);

  writeln('The slope is ', slope:0:2, ' and the y-intercept is ', y_intercept:0:2, '.');

  readln;
end.
```

We can ask [Bard](https://bard.google.com/) to take a guess at what the coding language might be.

:::{.query}
"What language is this code written in?"
:::


We can explore further to figure out what indicators tell Bard the language is Pascal.

:::{.query}
"How do you know this is Pascal?"
:::


It turns out there are multiple versions of Pascal. Since you will presumably need to work with this legacy code, you might want to know which version it is.

:::{.query}
"What version of Pascal is this?"
:::

## Example Three: Interpreting Regex

Regex (short for Regular Expressions) is a powerful tool used to describe patterns in text. It's a sequence of characters that define a search pattern. Regular expressions can be a powerful tool for data cleaning, text mining, and data validation. They are widely used in web development, data science, and other fields where text processing is important. They can also be tricky to understand at first because they involve a specific syntax that can be complex.

We can use [ChatGPT](https://chat.openai.com/) to explain regex in a bit of someone else's code.

```
x = sub(".*presentation/","",x)
```

:::{.query}
"What does this do?"
:::

```
x = sub("/d/e","/d",x)
```

:::{.query}
"What about this?"
:::


## Example Four: Understanding Variables and Functions

## Edge Cases

## Limitations?

## Hands-On Exercise

Now it's your turn to try. Let's say you were handed this bit of code to work with (and eventually modify), but first you need to figure out what's going on with it. Unfortunately, the original programmer left very little in the way of notes or annotation.

**Note**: This code is just an example and was written strictly for educational purposes.

```
use ode_solvers::{Euler, OdeMethod};
use plotters::prelude::*;
use std::fs::File;


const N: f64 = 1000000.0;  
const I0: f64 = 10.0;  
const R0: f64 = 0.0;   
const S0: f64 = N - I0 - R0;  
const BETA: f64 = 0.3;  
const GAMMA: f64 = 0.1;  

fn sir_model(t: f64, y: &[f64], v: f64) -> Vec<f64> {
    let s = y[0];
    let i = y[1];
    let r = y[2];
    let dsdt = -BETA * s * i / N - v * s;
    let didt = BETA * s * i / N - GAMMA * i;
    let drdt = GAMMA * i + v * s;
    vec![dsdt, didt, drdt]
}

fn main() {

    let mut solver = Euler::new(sir_model);
    solver.set_initial_condition(&[S0, I0, R0]);


    let root = BitMapBackend::new("sir_vaccination.png", (800, 600)).into_drawing_area();
    root.fill(&WHITE).unwrap();
    let mut chart = ChartBuilder::on(&root)
        .caption("SIR model with vaccination", ("sans-serif", 40))
        .set_label_area_size(LabelAreaPosition::Left, 60)
        .set_label_area_size(LabelAreaPosition::Bottom, 40)
        .build_cartesian_2d(0.0..100.0, 0.0..N)
        .unwrap();

    let mut data1 = vec![];
    for _ in 0..1000 {
        let y = solver.integrate(0.1, 0.0);
        data1.push((solver.time(), y[0], y[1], y[2]));
    }


    let vac_rate = 0.1;   
    let vac_coverage = 0.5;   
    let vac_num = vac_coverage * N;   
    let mut data2 = vec![];
    for i in 0..1000 {
        let t = i as f64 * 0.1;
        let v = if t >= 50.0 && t < 150.0 {vac_num * vac_rate} else {0.0};
        let y = solver.integrate(0.1, v);
        data2.push((solver.time(), y[0], y[1], y[2]));
    }


    chart
        .configure_mesh()
        .x_labels(10)
        .y_labels(10)
        .disable_x_mesh()
        .disable_y_mesh()
        .draw()
        .unwrap();
    chart
        .draw_series(LineSeries::new(
            data1.iter().map(|d|
```

**QUESTIONS:**

1. What language is the code written in?

1. What are two clues that tell you the language?

1. What is the overall task this code does?

1. What is a new feature you could add to the code?

1. How could you add that feature?

1. What does this bit of code do?

```
 let root = BitMapBackend::new("sir_vaccination.png", (800, 600)).into_drawing_area();
```

7. Why would a programmer set up a section of code like this?

```
fn sir_model(t: f64, y: &[f64], v: f64) -> Vec<f64> {
    let s = y[0];
    let i = y[1];
    let r = y[2];
    let dsdt = -BETA * s * i / N - v * s;
    let didt = BETA * s * i / N - GAMMA * i;
    let drdt = GAMMA * i + v * s;
    vec![dsdt, didt, drdt]
}
```

8. How are these variables initialized?

```
let s = y[0];
let i = y[1];
let r = y[2];
```

9. What are some other variables that could be added to this command to customize the output?

```
  chart
        .configure_mesh()
        .x_labels(10)
        .y_labels(10)
        .disable_x_mesh()
        .disable_y_mesh()
        .draw()
        .unwrap();
```



```r
devtools::session_info()
```

```
## ─ Session info ───────────────────────────────────────────────────────────────
##  setting  value                       
##  version  R version 4.0.2 (2020-06-22)
##  os       Ubuntu 20.04.5 LTS          
##  system   x86_64, linux-gnu           
##  ui       X11                         
##  language (EN)                        
##  collate  en_US.UTF-8                 
##  ctype    en_US.UTF-8                 
##  tz       Etc/UTC                     
##  date     2023-04-14                  
## 
## ─ Packages ───────────────────────────────────────────────────────────────────
##  package     * version date       lib source                            
##  assertthat    0.2.1   2019-03-21 [1] RSPM (R 4.0.5)                    
##  bookdown      0.24    2023-03-28 [1] Github (rstudio/bookdown@88bc4ea) 
##  bslib         0.4.2   2022-12-16 [1] CRAN (R 4.0.2)                    
##  cachem        1.0.7   2023-02-24 [1] CRAN (R 4.0.2)                    
##  callr         3.5.0   2020-10-08 [1] RSPM (R 4.0.2)                    
##  cli           3.6.1   2023-03-23 [1] CRAN (R 4.0.2)                    
##  crayon        1.3.4   2017-09-16 [1] RSPM (R 4.0.0)                    
##  curl          4.3     2019-12-02 [1] RSPM (R 4.0.3)                    
##  desc          1.2.0   2018-05-01 [1] RSPM (R 4.0.3)                    
##  devtools      2.3.2   2020-09-18 [1] RSPM (R 4.0.3)                    
##  digest        0.6.25  2020-02-23 [1] RSPM (R 4.0.0)                    
##  ellipsis      0.3.1   2020-05-15 [1] RSPM (R 4.0.3)                    
##  evaluate      0.20    2023-01-17 [1] CRAN (R 4.0.2)                    
##  fansi         0.4.1   2020-01-08 [1] RSPM (R 4.0.0)                    
##  fastmap       1.1.1   2023-02-24 [1] CRAN (R 4.0.2)                    
##  fs            1.5.0   2020-07-31 [1] RSPM (R 4.0.3)                    
##  glue          1.4.2   2020-08-27 [1] RSPM (R 4.0.5)                    
##  highr         0.8     2019-03-20 [1] RSPM (R 4.0.3)                    
##  hms           0.5.3   2020-01-08 [1] RSPM (R 4.0.0)                    
##  htmltools     0.5.5   2023-03-23 [1] CRAN (R 4.0.2)                    
##  httr          1.4.2   2020-07-20 [1] RSPM (R 4.0.3)                    
##  jquerylib     0.1.4   2021-04-26 [1] CRAN (R 4.0.2)                    
##  jsonlite      1.7.1   2020-09-07 [1] RSPM (R 4.0.2)                    
##  knitr         1.33    2023-03-28 [1] Github (yihui/knitr@a1052d1)      
##  lifecycle     1.0.3   2022-10-07 [1] CRAN (R 4.0.2)                    
##  magrittr      2.0.3   2022-03-30 [1] CRAN (R 4.0.2)                    
##  memoise       2.0.1   2021-11-26 [1] CRAN (R 4.0.2)                    
##  ottrpal       1.0.1   2023-03-28 [1] Github (jhudsl/ottrpal@151e412)   
##  pillar        1.9.0   2023-03-22 [1] CRAN (R 4.0.2)                    
##  pkgbuild      1.1.0   2020-07-13 [1] RSPM (R 4.0.2)                    
##  pkgconfig     2.0.3   2019-09-22 [1] RSPM (R 4.0.3)                    
##  pkgload       1.1.0   2020-05-29 [1] RSPM (R 4.0.3)                    
##  prettyunits   1.1.1   2020-01-24 [1] RSPM (R 4.0.3)                    
##  processx      3.4.4   2020-09-03 [1] RSPM (R 4.0.2)                    
##  ps            1.4.0   2020-10-07 [1] RSPM (R 4.0.2)                    
##  R6            2.4.1   2019-11-12 [1] RSPM (R 4.0.0)                    
##  readr         1.4.0   2020-10-05 [1] RSPM (R 4.0.2)                    
##  remotes       2.2.0   2020-07-21 [1] RSPM (R 4.0.3)                    
##  rlang         1.1.0   2023-03-14 [1] CRAN (R 4.0.2)                    
##  rmarkdown     2.10    2023-03-28 [1] Github (rstudio/rmarkdown@02d3c25)
##  rprojroot     2.0.3   2022-04-02 [1] CRAN (R 4.0.2)                    
##  sass          0.4.5   2023-01-24 [1] CRAN (R 4.0.2)                    
##  sessioninfo   1.1.1   2018-11-05 [1] RSPM (R 4.0.3)                    
##  stringi       1.5.3   2020-09-09 [1] RSPM (R 4.0.3)                    
##  stringr       1.4.0   2019-02-10 [1] RSPM (R 4.0.3)                    
##  testthat      3.0.1   2023-03-28 [1] Github (R-lib/testthat@e99155a)   
##  tibble        3.2.1   2023-03-20 [1] CRAN (R 4.0.2)                    
##  usethis       1.6.3   2020-09-17 [1] RSPM (R 4.0.2)                    
##  utf8          1.1.4   2018-05-24 [1] RSPM (R 4.0.3)                    
##  vctrs         0.6.1   2023-03-22 [1] CRAN (R 4.0.2)                    
##  withr         2.3.0   2020-09-22 [1] RSPM (R 4.0.2)                    
##  xfun          0.26    2023-03-28 [1] Github (yihui/xfun@74c2a66)       
##  yaml          2.2.1   2020-02-01 [1] RSPM (R 4.0.3)                    
## 
## [1] /usr/local/lib/R/site-library
## [2] /usr/local/lib/R/library
```
