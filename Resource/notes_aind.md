0. The Pac-Man project [link](http://ai.berkeley.edu/project_overview.html)
1. Search Strategy ,  Heuristic = Informed


# Planing

 For more information on uninformed planning algorithms and informed search, please, check out the links below:
  
 -   https://www.ics.uci.edu/~rickl/courses/cs-171/cs171-lecture-slides/cs-171-03-UninformedSearch.pdf.
    http://cs.lmu.edu/~ray/notes/usearch/.
    https://fr.slideshare.net/ameykerkar/control-strategies-in-ai.
    http://www.sanfoundry.com/artificial-intelligence-mcqs-informed-search-exploration-1/.

Python Visualisation Tools

- 
    https://seaborn.pydata.org/index.html \
    http://pygal.org/en/stable/


Need more effort thinking:

- Extra Tips

- Here are some questions to consider:
- Why does DFS not provide an optimal plan for this case?
- Which are the fastest and slowest uninformed algorithms? Why?
- Which are the fastest and slowest heuristic searches? Why?
- Which algorithms (uninformed and heuristic) have the lowest node expansions and goal tests? Why? 
- What does this mean for the performance in this problem?
- Please don't forget to site your references like you did in your research report
 
# Probability

1. Dynamic Time Warping [link](http://wearables.cc.gatech.edu/paper_of_week/DTW_myths.pdf)  
2. Rabiner's  Tutorial on hidden Markov Models and selected applications in speech recognition [link](http://www.cs.ubc.ca/~murphyk/Bayes/rabiner.pdf) [errata](http://alumni.media.mit.edu/~rahimi/rabiner/rabiner-errata/)
3. HMM Tookit [link](http://htk.eng.cam.ac.uk/)
4. Segmentally Boosted HMMs [Gesture and Activity Recognition Tookkit](https://wiki.cc.gatech.edu/ccg/projects/gt2k/gt2k) [Pei Yin's dissertation](https://smartech.gatech.edu/handle/1853/33939)
6. Baum-Welch is one of Expectation-Maximization algorithm [link](https://en.wikipedia.org/wiki/Baum%E2%80%93Welch_algorithm)  
7. hmmlearn library [link](https://hmmlearn.readthedocs.io/en/latest/) 
   -  The HMM is completely determined by π, A and θ, how to get them , refer to Baum-Welch EM algorithm in wiki [link](https://en.wikipedia.org/wiki/Baum%E2%80%93Welch_algorithm) 
0. Log Likelihood and Likelihood in Gaussian Distribution [link](https://math.stackexchange.com/questions/892832/why-we-consider-log-likelihood-instead-of-likelihood-in-gaussian-distribution)
0. Bayesian Information Criterion(BIC) [link]( http://www2.imm.dtu.dk/courses/02433/doc/ch6_slides.pdf)
    - select the model with the lowest Bayesian Information Criterion(BIC) score
    http://www2.imm.dtu.dk/courses/02433/doc/ch6_slides.pdf
    - Bayesian information criteria: BIC = -2 * logL + p * logN
0.  Discriminative Information Criterion [link]
    - Biem, Alain. "A model selection criterion for classification: Application to hmm topology optimization."
    Document Analysis and Recognition, 2003. Proceedings. Seventh International Conference on. IEEE, 2003.
    http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.58.6208&rep=rep1&type=pdf
    https://pdfs.semanticscholar.org/ed3d/7c4a5f607201f3848d4c02dd9ba17c791fc2.pdf
    - DIC = log(P(X(i)) - 1/(M-1)SUM(log(P(X(all but i))