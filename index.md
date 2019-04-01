# Supplementary Materials for the Tinkering Humanist Series and Related Workshops


This repository is intended to supplement the workshops offered through the Digital Humanities Center at Purdue University. In addition to the code and datasets used for different sessions, you'll find information about additional resources to help you get started with a given method or application. 

## Workshop Materials

### Text Analysis with R - [Code/Data (All Sessions)](), [General Resource List]()
The zip file linked above includes all of the code and data for all three sessions in the series, and the resource list is a more general collection of links concerning text analysis and R. For detailed comments and links concerning each session's topic, see below.

**Session I: Introduction - [Code/Data]()**


In Session I, we discussed some of the basic steps that go into any text analysis project, explored why cleaning and preprocessing data is important, and performed some basic word frequency calculations. Most of the code included for this session was adapted from Chapters 2 and 3 of Matthew Jockers' [*Text Analysis with R for Students of Literature*](https://purdue-primo-prod.hosted.exlibrisgroup.com/primo-explore/fulldisplay?docid=PURDUE_ALMA51683474750001081&context=L&vid=PURDUE&search_scope=everything&tab=default_tab&lang=en_US). As we noted, however, there are many ways to accomplish these tasks. You might compare Jockers' steps to those of [*Text Mining with R*](https://purdue-primo-prod.hosted.exlibrisgroup.com/primo-explore/fulldisplay?docid=PURDUE_ALMA51719072750001081&context=L&vid=PURDUE&search_scope=everything&tab=default_tab&lang=en_US) by Julia Silge and David Robinson, which uses a "tidy" approach to the basics of text analysis. The tutorial ["Basic Text Processing in R"](https://programminghistorian.org/en/lessons/basic-text-processing-in-r) by Taylor Arnold and Lauren Tilton covers similar ground, or consult their book [*Humanities Data in R*](https://purdue-primo-prod.hosted.exlibrisgroup.com/primo-explore/fulldisplay?docid=PURDUE_ALMA51719072750001081&context=L&vid=PURDUE&search_scope=everything&tab=default_tab&lang=en_US) . All of the books above are available as e-books through Purdue Libraries.

**Session II: Sentiment Analysis and Syuzhet - [Code/Data](), [Files]()**


In Session II, we explored sentiment analysis using Jockers' R package `syuzhet`. It is always good to consult the documentation for a package to understand its functions, what arguments they take, etc. The documentation for `syuzhet` is [here](https://www.rdocumentation.org/packages/syuzhet/versions/1.0.4). Much of the code for the session was adapted from the package's vignette, where Jockers some of the more technical aspects of the package and walks through several functions we did not cover. When it was created, `syuzhet` received a lot of interest and criticism, much of which is worthy of careful reading. Check out Jockers [own blog posts](http://www.matthewjockers.net//?s=syuzhet&search=Go) on the package, and [a literature professor's critiques](https://annieswafford.wordpress.com/syuzhet-blog-posts/).

You may also want to read up on the different lexicons that you can utilize through `syuzhet`:

* The "afinn" lexicon was constructed by Finn Arup Nielsen. The full wordlist, a collection of apers, and links to tools using afinn can be found [at this wiki](http://neuro.compute.dtu.dk/wiki/AFINN). 
* The "bing" opinion lexicon can be found at the website of its namesake, [Bing Liu](https://www.cs.uic.edu/~liub/FBS/sentiment-analysis.html), along with links to his research and other resources of interest. 
* The NRC word-emotion lexicon and its documentation, constructed by Saif Mohammad, can be accessed [through his website](http://saifmohammad.com/WebPages/NRC-Emotion-Lexicon.htm). 

Unfortunately, there is not a great deal of information about the syuzhet lexicon itself. You can, however, access the wordlist through the package's `get_sentiment_dictionary()` function. If you want to look at a specific word's value, you can use the subset function:

`subset(get_sentiment_dictionary(), word=="abandon")`

You could also use the same function to identify words of a certain value.

`subset(get_sentiment_dictionary(), value==-1.00)`

But if you want to examine the list as a whole, perhaps write the file to a csv for future use (providing your own file path and file name below)
```
syuzhet_wordlist <- get_sentiment_dictionary() %>%
  write.csv(file = "syuzhet_wordlist.csv")
```
There are other R packages devoted to sentiment analysis. Read about some of them in this recent article, ["A review of sentiment computation methods with R packages," by Maurizio Naldi](https://arxiv.org/pdf/1901.08319.pdf).


**Session III: Stylometry and Stylo - [Code/Data]()**


In Session III, we learned about stylometry and played with author attribution using the `stylo` package. The team that put `stylo` together has provided a variety of helpful documentation and descriptive material. Check out the [Usage section of their github repository](https://github.com/computationalstylistics/stylo#usage) for a good list of materials at different skill levels. You can browse the [Computational Stylistics Group website](https://computationalstylistics.github.io) for even more reading from the same team, including information about the ["rolling" functions](https://sites.google.com/site/computationalstylistics/projects/testing-rolling-stylometry). For a thorough examination of distance measurement in relation to stylometry, see "Understanding and explaining Delta measures for authorship attribution"(https://doi.org/10.1093/llc/fqx023) in *Digital Scholarship in the Humanities*, Vol. 32, Issue supplement 2. Finally, [this video about Principal Components Analysis](https://www.youtube.com/watch?v=jZ532ucT6Ik) may help demystify that particular type of analysis.

A tutorial at the [Programming Historian](https://programminghistorian.org/en/lessons/introduction-to-stylometry-with-python) walks you through doing similar tasks with Python. It also discusses the Federalist Papers in some detail.  
