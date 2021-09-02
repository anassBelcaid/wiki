# Jekyll


## Al-folio theme

this [theme](https://github.com/alshedivat/al-folio/) works for now with only
**ruby 2.7**.

```shell
rbenv shell 2.7
```

in order to activate a ruby 2 version.


### Scientific notes

This a an example for the front 


```markdown
---
layout: distill
title: "Lecture 2: Bayesian Networks"
description: Overview of Bayesian Networks, their properties, and how they can  be helpful to model the joint probability distribution over a set of random variables. Concludes with a summary of relevant sections from the textbook reading.
date: 2019-01-16

lecturers:
  - name: Eric Xing
    url: "https://www.cs.cmu.edu/~epxing/"

authors:
  - name: Cathy Su
    url: "https://ceesu.github.io"   
  - name: Angel C. Hernandez
    url: "https://github.com/ahernandez105"
  - name: Mark Cheung
    url: "#"
  - name: Xueqian Li
    url: "#"

editors:
  - name: Maruan Al-Shedivat  # editor's full name
    url: "https://www.cs.cmu.edu/~mshediva/"  # optional URL to the editor's homepage
```

### Math

1. You can write simple inline math by surrending it between **$**.
2. Also, you can create a special block:
```
<d-math block>
...
</d-math>
```

### Bibliography


You can use the latex bibliography system by setting up a file in
*./assets/bibliography/* and then use the following syntax to refere to it.

```
<d-cite key="key" ></d-cite>
```
