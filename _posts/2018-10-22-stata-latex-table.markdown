---
layout: post
title:  "Automated (latex) table generation using Stata"
date:   2018-05-17 14:05:21 +0800
tags: jekyll update
color: rgb(77,203,200)
cover: '../assets/postTable2.jpg'
subtitle: 'Exporting latex-ready tables from Stata :-)'
---
Exporting regression tables to latex from Stata is pretty straightforward thanks to user-written ado files such as `estout` (my personal favorite). However, sometimes a more flexible solution is needed. For example, you may want to generate summary statistics, or maybe you want to present a non-standard regression table. This mini-tutorial is tailored to these kind of situations, and it's based on the `file` stata command. Next we will start with a simple example to introduce the command basics, and then we will look a more elaborated one to show some tricks that can further boost its flexibility.

## A simple example
In order to give a general feel on how this method works, lets see a example:
```
file open sm using "`savename'", write replace
file write sm "\begin{tabular}{lccc}\toprule"_n
file write sm " & \multicolumn{3}{c}{Very Interesting Table} \\ \cmidrule(l){2-4}"_n
file write sm " & (1) & (2) & (3) \\ \midrule"_n
file write sm " Row \# 1 Name &  Value \# 1 &  Value \# 2 &  Value \# 3 \\"_n
file write sm "\bottomrule"
file write sm "\end{tabular}"
file close sm
```
From this silly example we can see the basics behind `file` usage. .


