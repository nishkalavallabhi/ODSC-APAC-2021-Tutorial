NLP without a readymade labeled dataset
========================================================
author: Sowmya Vajjala
date: 15th September 2021
autosize: true
navigation: section

Tutorial @ ODSC-APAC, 2021


<style>
.small-code pre code {
  font-size: 1em;
}
</style>

Tutorial Overview
========================================================
- NLP: Overview
- Collecting, Labeling and Augmenting datasets
- Generating annotated data and modeling with it
- What, next?  
- Conclusion

About Me
========================================================
- Researcher at National Research Council, Canada
- Past experiences: Industry, Academic Research, Teaching, Mentoring etc. 
- Co-authored a book recently: "Practical Natural Language Processing - A Comprehensive Guide to Building Real-World NLP Systems"

About You
========================================================
- You know something about NLP
- You perhaps already faced this issue with labeled datasets
- You don't already know everything about addressing this issue :-)

NLP: An Overview
========================================================
type: section


========================================================
![EverydayNLP](figures/everydaynlp.png) 


Some common NLP use cases
========================================================
![NLPSurvey](figures/nlpsurvey.png) 

source: [2020 NLP survey](https://gradientflow.com/2020nlpsurvey/)


NLP System Development Pipeline
========================================================
![Pipeline](figures/pipeline.png) 

source: Chapter 2 in practicalnlp.ai


Data and NLP
========================================================
  - The starting point of any modern NLP system is data. 
  - However, in many research and real-world scenarios, when we encounter a new problem, we don't have such ready made datasets that suit our need. 
  - What should we do, then? 
  - Why do we need data, anyway?
  - What kind of data do we really need for NLP? 
  - how do we collect such data?

So, why do we need data, anyway?
========================================================
incremental: true

  - Modern NLP is heavily machine learning driven and machine learning approaches typically require lots and lots of examples to "train" on and learn a task.
  - Assuming we are "engineering" everything manually, we still need some kind of curated data to evaluate our approach for its accuracy and coverage.
 - Even if we are just using some off-the-shelf solution, we need to know how good it is for our scenario!
 
- So, good quality datasets are very (very) important for building any NLP system. 

What kind of data do we really need for NLP?
========================================================
- Different kinds of NLP systems need different kinds of data. 
- Sometimes, all we need are large collections of documents without any additional information (e.g., tasks such as language modeling, topic modeling etc). 
- But in many cases, we need large collections of labeled data i.e., input -> output pairs. 
- Here are some examples:
    - sentence-translated sentence pairs (machine translation)
    - spam/non-spam emails (an example text classification)
    - question-answer pairs
    - sentence -> names of entities in it, relations between them etc (information extraction)


What kind of data do we need? - 2
========================================================
   - Quantity: Typically, "learning" methods are data hungry. The more, the better, although it may plateau at some point. (What is large?)
    - Quality: Garbage in $->$ Garbage out. We can't take **anything** we can lay hands on. (Why?) 
    - Data without ethical concerns such as using data without consent, keeping personally identifiable information, racial/gender bias in training examples etc. (Why is this important?)
    - Variety: Data that is of the same kind as our end use case (e.g., legal docs for legal use cases) (Why?) 
    
    
Collecting, Labeling and Augmenting datasets
========================================================
type: section
    
How do we obtain labeled data? - 1
========================================================
incremental: true

   - use available data sets with some labeling:
      - scraping websites (forums, wikipedia, news etc)
      - social media content (tweets etc)
      - internal data (logs, customer support messages etc)
    - advantage:
      - We don't have to setup new labeling mechanisms
      - potentially large amounts of data can be collected
    - disadvantage:
      - quality control?
    - Note that this is not your most common scenario in real world
      
How do we obtain labeled data? - 2
========================================================

collect your own data: surveys, user studies, crowd sourcing etc. 
   
<img src="figures/Doccano.png" alt="doccano" height="250" width="600"/>
<p style="font-size:30px">source:<a href="https://github.com/doccano/doccano">Doccano</a></p>

- Advantage: Best suited to our requirements
- Disadvantage: It can be very expensive/time consuming to get large amounts needed for ML/DL models. 

Label studio-Example
========================================================
![label studio](figures/label-studio-1.png)

Label studio-Example
========================================================
![label studio](figures/label-studio-2.png)

Label studio-Example
========================================================
![label studio](figures/label-studio-3.png)

Label studio-setting things up
========================================================
![label studio](figures/label-studio-4.png)

Label studio - export the labeled dataset
========================================================
![label studio](figures/label-studio-5.png)

Data labeling with Label Studio - input and output
========================================================
![label studio](figures/label-studio-0.png)
![label studio](figures/label-studio-last.png)


Data labeling - conclusion
========================================================
- I just showed a simple example, but there are a whole lot of annotation support tools for NLP tasks.
- [This listing by Doccano](https://github.com/doccano/awesome-annotation-tools) provides a comparison in terms of features, pricing, and the kind of NLP tasks that the tools support. 

Creating more data: Data Augmentation 
========================================================
Generate new data by changing existing (labeled) data slightly.
- Replacing words with synonyms
- Back translation 
- Random insertion/deletion of words
- Swapping words
- Simulated typos/OCR errors etc. 
etc.

Some python libraries: [nlpaug](https://github.com/makcedward/nlpaug), [eda_nlp](https://github.com/jasonwei20/eda_nlp), [snorkel](https://snorkel.org)

Data Augmentation: Example 1
========================================================
Replacing words with synonyms (of different kinds) 

![augmentation1](figures/augmentation1.PNG)

source: [https://github.com/makcedward/nlpaug](nlpaug)


Data Augmentation: Example 2 
========================================================
Back translation

![backtranslation](figures/backtranslation.PNG)

[https://amitness.com/2020/05/data-augmentation-for-nlp/](Source)

<!-- may be add some code examples here? --> 


Modeling with small(-er) datasets: Issues
========================================================
- We can't go too far with small datasets, though. 

[http://ai.stanford.edu/blog/weak-supervision](Stanford AI Lab blog)

![methods](figures/methods.png)

Active Learning
========================================================
![activelearning](figures/al.png)

[source: Professor Tom Mitchell's course slides](https://www.cs.cmu.edu/~tom/10701_sp11/recitations/Recitation_13.pdf)

Semi-supervised Learning
========================================================
![semisupervised](figures/semisup.png)
[source](https://www.enjoyalgorithms.com/blogs/supervised-unsupervised-and-semisupervised-learning)

Weak Supervision
========================================================
<img src="figures/weaks.png" alt="weaksupervision" height="500" width="600"/>

[source - skweak Python library](https://github.com/NorskRegnesentral/skweak)

Transfer Learning
========================================================
![transferlearning](figures/tl.png)
[source - ruder.io](https://ruder.io/transfer-learning/)

A scenario combining them all
========================================================
![HIL](figures/hil.png)

source: Chapter 1 in ["Human-in-the-Loop Machine Learning " by Robert Munro.] (https://www.manning.com/books/human-in-the-loop-machine-learning)

Practical Advice-1
========================================================
- Have some idea of what you want.
- Annotate a small amount of data
- Evaluate an off-the shelf solution if it exists. 
- Evaluate transfer learning if a similar model is available

Practical Advice-2
========================================================
- Weak supervision
- Semi-supervised learning
- Active learning
- More elaborate models


A working example
========================================================
- problem: text classification ... sentiment classification
- why I chose such a common one?
- no data NLP: google cloud example - how good is it on the test sentences?
- transfer learning - use an existing pre-trained model or sentiment model
- weak supervision - snorkel
- comparison with a "regular" scenario


<!--
https://github.com/nishkalavallabhi/SfSCourseJan2021/blob/main/slides-tex/NLPWithoutData-DataLabeling.tex
-->

No data NLP: using off the shelf solutions
========================================================
type: section

<!-- google cloud content classification example and Bing MT? -->
<!-- A slide on advantages and disadvantages -->


