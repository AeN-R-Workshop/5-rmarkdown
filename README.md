
# Introduction to R markdown - A step by step guide for distracted scientists

## Aims of the workshop

Together we will develop a Rmarkdown file which includes most of the elements of a scientific report article. Starting with basic formatting, we will add more features: equations, figures, images, bibliographic references, code-folding, equations, and automated changes to the filename.
In the end, you will have a document which can serve either as a template and reference for your future use of Rmarkdown. 

You can use most of the workshop's code with other Rmarkdown packages and extension (Distill, Bookdown, etc). We will take a closer look at the packages distill and bookdown.


## Requirements 

If you want to add images to your Rmarkdown file, you need to place the image in the same folder (or a subfolder) as the .Rmd file. In the workshop we will use **bird.JPG** as example image. 

You will also need to place the **library.bib** file in the same folder as your Rmd file, if you want to try out the reference function during the workshop.

To be able to follow along without hiccups I recommend to install or update the following packages:

**Rmarkdown** 

```
install.packages('rmarkdown')
```

**Knitr** and **KableExtra** - These packages allow us to include "kable"-tables, which look quite nice and include some interactivity. 

```
install.packages('knitr')
install.packages('kableExtra')
```


**Tinytex** in case you have not already installed a LaTeX software like MiKTeX. It is needed to produce pdf documents directly. 

```
install.packages('tinytex')
tinytex::install_tinytex()  # install TinyTeX
```

**Bookdown** This is a Rmarkdown package which adds some extra functionality, and allows you to convert your work into a book and other formats

```
install.packages("bookdown")
```

**Distill** This is a Rmarkdown package which adds some extra functionality and a RMD template which contains already some of the things you will learn today. 

```
install.packages("distill")
```

**mgcv** This a package for generalized additive models, which is used in one of the examples. Not strictly necessary for the workshop but anyhow good to have.

```
install.packages("mgcv")
```

**plotly** This another plotting package, which besides other things, can enhancec ggplot with some interactivity. 

```
install.packages("plotly")
```


## Copy and paste 

The following section has some code blocks which might be too tedious to write yourself during the workshop, so you can just copy and paste them from here. 

### Sample equation

Probably complete mathematical nonsense, but shows some common syntax of LaTeX equations

```
$$ \lim\limits_{v \to \infty} \exp(-\frac{x}{n}) = 0 $$
```


### Update the date

```
date: "`r Sys.Date()`"
```

### Some formatted table
```
df %>% 
  round(.,2) %>% 
  mutate(x = color_tile("white", "green")(x),
        y = ifelse(y < 5,
                  cell_spec(y, "html", color = "black", bold = TRUE),
                  cell_spec(y, "html", color = "grey"))) %>% 
  kable("html", escape = FALSE, caption = "This is the data you were waiting for.") %>%
  kable_styling(font_size = 10) %>% 
  row_spec(0, background = 'lightgrey', bold = TRUE) %>%
  scroll_box(width = "100%", height = "200px") 
 ```


### Add date to rendered file

```{}
knit: (function(inputFile, encoding) { rmarkdown::render(inputFile, encoding = encoding, output_file = paste0(substr(inputFile,1,nchar(inputFile)-4),Sys.Date(),'.html')) })
```

### Tabs, sorts the following subheadings into tabs

```{}
{.tabset .tabset-fade .tabset-pills}
```


## Links that might be helpful

* R markdown introduction 1: https://bookdown.org/yihui/rmarkdown-cookbook/
* R markdown introduction 2: https://bookdown.org/yihui/rmarkdown/
* Latex syntax for equations and symbols https://en.wikibooks.org/wiki/LaTeX/Mathematics
* Themes: https://www.datadreaming.org/post/r-markdown-theme-gallery/
* Bookdown: https://bookdown.org/yihui/bookdown/
* Distill: https://rstudio.github.io/distill/
* Xaringhan: https://bookdown.org/yihui/rmarkdown/xaringan.html
