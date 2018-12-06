## Platform and competition

1. 天池 练习赛 https://tianchi.aliyun.com/
2. kaggle
3. HackerRank

## Done

1. TBD Data Science Bowl 2017 CT [link](https://www.kaggle.com/c/data-science-bowl-2017/kernels?sortBy=hotness&group=everyone&pageSize=20&competitionId=6004) [Intro](http://www.sohu.com/a/138840776_610300)

## Practical suggestions, Tuning

### Overfitting

1. More data - Data Augmentation
2. Smaller NET - Bad generalization 
3. Train - Early Stoppin
4. regularization
5. Dropout
6. Batch Normalization
7. Cross - Validation [EliteDataSciense](https://elitedatascience.com/machine-learning-iteration#micro)

### Underfitting


### 1. How to choose RNN gate unit  

1. Empirical Evaluation of Gated Recurrent Neural Networks on Sequence Modeling [pdf](http://proceedings.mlr.press/v37/jozefowicz15.pdf)
2. An Empirical Exploration of Recurrent Network Architectures [pdf](http://proceedings.mlr.press/v37/jozefowicz15.pdf)
3. Visualizing and Understanding Recurrent Networks [pdf](https://arxiv.org/abs/1506.02078)
4. Understanding LSTM Networks [link](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)
5. Massive Exploration of Neural Machine Translation Architectures [paper](https://arxiv.org/abs/1703.03906v2)
6. Practical recommendations for gradient-based training of deep architectures [paper](https://arxiv.org/abs/1206.5533)
7. Deep Learning book - chapter 11.4: Selecting Hyperparameters [book](http://www.deeplearningbook.org/contents/guidelines.html)
8. Neural Networks and Deep Learning book - Chapter 3: How to choose a neural network's hyper-parameters [book](http://neuralnetworksanddeeplearning.com/chap3.html#how_to_choose_a_neural_network's_hyper-parameters) 
9. Efficient BackProp (pdf) [pdf](http://yann.lecun.com/exdb/publis/pdf/lecun-98b.pdf)

### 2. Example RNN Architectures

Application|Cell|Layers|Size|Vocabulary|Embedding Size|Learning Rate|paper
-|:-:|:-:|:-:|:-:|:-:|:-:|-:
Speech Recognition (large vocabulary)| LSTM| 5, 7| 600, 1000| 82K, 500K| --| --| [paper](https://arxiv.org/abs/1610.09975)
Speech Recognition| LSTM| 1, 3, 5| 250| --| --| 0.001| [paper](https://arxiv.org/abs/1303.5778 )
Machine Translation (seq2seq)| LSTM| 4| 1000| Source: 160K, Target: 80K| 1,000| --| [paper](https://arxiv.org/abs/1409.3215)
Image Captioning| LSTM| --| 512| --| 512| (fixed)| [paper](https://arxiv.org/abs/1411.4555)
Image Generation| LSTM| --| 256, 400, 800| --| --| --| [paper](https://arxiv.org/abs/1502.04623)
Question Answering| LSTM| 2| 500| --| 300| --| [paper](http://www.aclweb.org/anthology/P15-2116)
Text Summarization| GRU| 200| --| Source: 119K, Target: 68K| 100| 0.001| [paper](https://pdfs.semanticscholar.org/3fbc/45152f20403266b02c4c2adab26fb367522d.pdf)

3.How to generate a good word embedding" Lai , Siwei, IEEE Intelligence System 31.6(2016): 5-14 [link](https://arxiv.org/abs/1507.05523)

4.Systematic evaluation of CNN advances on the ImageNet[paper](https://arxiv.org/abs/1606.02228)

5.Tune your network [link](https://pcc.cs.byu.edu/2017/10/02/practical-advice-for-building-deep-neural-networks/) 

## Solution Paradigm
1. Multi-label questions ?