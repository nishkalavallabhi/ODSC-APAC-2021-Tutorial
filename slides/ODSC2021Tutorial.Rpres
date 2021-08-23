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
- Modeling with small datasets: an overview
- A case study: code walk through  
- Conclusion
(I will talk first, show next.)

Code, slides: [https://github.com/nishkalavallabhi/ODSC-APAC-2021-Tutorial](https://github.com/nishkalavallabhi/ODSC-APAC-2021-Tutorial)

These slides: [https://rpubs.com/vbsowmya/odsc2021](https://rpubs.com/vbsowmya/odsc2021)

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

Weak supervision: an introduction
========================================================
incremental:true

Generally, most 'learning' methods used in NLP are data hungry. However, it is time consuming and also expensive to hand label so much of data for each new problem. 

Sometimes, we may have to update existing labels to suit changed guidelines or just update the dataset etc. (not so uncommon in real world). How do we handle the costs/time taken? 

"Weak supervision" refers to a machine learning approach which relies on "imprecise" training data, which is potentially "generated" automatically. 

An approach: write code based on observed patterns in data to label subsets of unlabeled data.... and then use this code to create labeled training data for our ML model


"Practical" Weak Supervision -1
========================================================
<img src="figures/weaks.png" alt="weaksupervision" height="500" width="600"/>

[source - skweak Python library](https://github.com/NorskRegnesentral/skweak)

"Practical" Weak Supervision -2
========================================================
<img src="figures/snorkelradiologyexample.png" alt="weaksupervision" height="500" width="600"/>

[Source](https://db.cs.washington.edu/events/workshop/2019/slides/alex-ratner.pdf)

How can this work in practice: Snorkel
========================================================
<img src="figures/3snorkelops.png" alt="weaksupervision" height="500" width="600"/>

[Source](https://db.cs.washington.edu/events/workshop/2019/slides/alex-ratner.pdf)

Sounds good! Does it really work, though?
========================================================
<img src="figures/snorkelrealworld.png" alt="weaksupervision" height="500" width="600"/>

Sounds good! Does it really work, though?
========================================================

<img src="figures/snorkelwild.png" alt="weaksupervision" height="500" width="600"/>

source: https://www.snorkel.org/resources/


Other methods: Active Learning
========================================================
![activelearning](figures/al.png)

[source: Professor Tom Mitchell's course slides](https://www.cs.cmu.edu/~tom/10701_sp11/recitations/Recitation_13.pdf)

Other methods: Semi-supervised Learning
========================================================
![semisupervised](figures/semisup.png)
[source](https://www.enjoyalgorithms.com/blogs/supervised-unsupervised-and-semisupervised-learning)

Other methods: Transfer Learning
========================================================
![transferlearning](figures/tl.png)
[source - ruder.io](https://ruder.io/transfer-learning/)

A scenario combining them all
========================================================
![HIL](figures/hil.png)

source: Chapter 1 in ["Human-in-the-Loop Machine Learning " by Robert Munro.] (https://www.manning.com/books/human-in-the-loop-machine-learning)

Practical Advice-1
========================================================
incremental: true

You have no data to start with.

- Understand your requirements, and create a small, high-quality, manually inspected, labeled dataset (e.g., using label studio like tools)
- Evaluate an off-the shelf solution if it exists. 
- Create automatically labeled data and build a model using weak supervision, evaluating with your high quality test data.

Practical Advice-2
========================================================
incremental: true

You managed to get some labeled data through automatic labeling or other means.
Then, what?
- Evaluate transfer learning if a similar model is available
- Semi-supervised learning and Active learning

Slowly, you built up a large collection of labeled or pseudo-labeled data:
- Explore more sophisticated ML/DL models

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

Sentiment Analysis with Azure Text Analytics
========================================================

[source](https://docs.microsoft.com/en-us/azure/cognitive-services/text-analytics/how-tos/text-analytics-how-to-sentiment-analysis?tabs=version-3-1)

- "Sentiment Analysis in version 3.x applies sentiment labels to text, which are returned at a sentence and document level, with a confidence score for each."

- labels: positive, negative, mixed, neutral

- "Confidence scores range from 1 to 0. Scores closer to 1 indicate a higher confidence in the label's classification, while lower scores indicate lower confidence."

Sentiment Analysis with Azure Text Analytics
========================================================
Things to think about: 
- We need a model with only positive/negative labels. What should we do about mixed/neutral? 
- Is this a permanent solution, or should we start thinking about collecting labeled data eventually?

No Data NLP - Example
========================================================
![azure1](figures/azure1.png)

![azure1](figures/azure2.png)

No Data NLP - Example
========================================================
![azure1](figures/azure3.png)

![azure1](figures/azure4.png)

No Data NLP - Conclusion
========================================================

Advantage: 
- You don't have to worry about setting stuff up, building and maintaining the sentiment analyzer etc.
- You can quickly get an MVP up and running.

Disadvantages:
- This only works if you have problem that exactly meets the specifications of such an available API
- No possibility of customization/modification
- Depending on how much you use, costs may escalate
- You still have to think whether this approach is a long term solution for your problem.


Weak supervision, with Snorkel: an example
========================================================




<!-- google cloud content classification example and Bing MT? -->
<!-- A slide on advantages and disadvantages -->


