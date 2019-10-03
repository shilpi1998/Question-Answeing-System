# Question-Answeing-System
## Implementation<br>

The primary aim of the system is to produce an appropriate answer to the question asked by the user for a
given context. The secondary aim is to facilitate query reformulation when searching the query.<br>

## Tools and Technologies<br>
The first decision to make when implementing the system was to decide upon the programming languages, technologies and libraries that would be used.
Python 3.6 was chosen as the language of choice for the project. Python is a widely used high-level programming language whose syntax emphasizes code readability and maintainability. Most importantly, it has a strong developer community behind it, resulting in a large collection of excellent third-party libraries, including the following:<br>
The Natural Language Toolkit (nltk) is an open source library for the Python programming language. It comes with a hands-on guide that introduces topics in computational linguistics as well as programming fundamentals for Python which makes it suitable for linguists who have no deep knowledge in programming, engineers and researchers that need to delve into computational linguistics.<br>
 Scikit-learn is a free software machine learning library for the Python programming language. It features various classification, regression and clustering algorithms including support vector machines, random forests, gradient boosting, k-means and DBSCAN, and is designed to interoperate with the Python numerical and scientific libraries NumPy and SciPy.<br>
 Keras is a high-level neural networks API, written in Python and capable of running on top of TensorFlow, CNTK, or Theano. It was developed with a focus on enabling fast experimentation. Being able to go from idea to result with the least possible delay is key to doing good research.<br>

## Data Collection<br>
To investigate the efficiency of our project we use the Stanford Question Answering Dataset (SQuAD), a new reading comprehension dataset consisting of 100,000+ questions posed by crowd workers on a set of Wikipedia articles, where the answer to each question is a segment of text from the corresponding reading passage. We analyze the dataset to understand the types of reasoning required to answer the questions.<br>

## Data Preprocessing<br>
The dataset extracted from squad can’t be used as it is in our neural network model. For suitable features to be utilized data has to be preprocessed.
Firstly, the data is retrieved from the stored json file into three different lists: paragraph, question and answer. Now, paragraph and questionare treated as input and answers as output. These passages are then tokenized with tokenize function and are broken into tokens. For this keras tokenizer library is used. We have raw text,
but we want to make predictions on a per-word basis. This means we must tokenize our comments into sentences, and sentences into words.<br>

## Vectorization of Features and Dictionary formation<br>
With the help of Tokenized words a dictionary is formed containing passages, questions and answers. In which each word is mapped with a unique index. Vectorization is performed with the help of one hot encoding. One hot encoding is a representation of categorical variables as binary vectors. This first requires that the categorical values be mapped to integer values. Then, each integer value is represented as a binary vector that is all zero values except the index of the integer, which is marked with a 1.<br>

## Training Seq2Seq Model<br>
In this phase the extracted features from our dataset are passed to Seq2seq model to generate desired output.<br>

## Sequence to Sequence Model<br>
A typical sequence to sequence model has two parts – an encoder and a decoder. Both the parts are practically two different neural network models combined into one giant network. Broadly, the task of an encoder network is to understand the input sequence, and create a smaller dimensional representation of it. This representation is then forwarded to a decoder network which generates a sequence of its own that represents the output.<br>
The encoding and decoding parts are usually composed of RNN cells. Long Short Term Memory cells were very efficient to deal with vanishing gradient issues. LSTM cells help the network capture long term dependencies and therefore exploit long sequences. Attention mechanisms are an extension to the encoder-decoder model. It helps at each step the decoder with a context vector pointing out where the relevant information about the next token is located.<br>

## Long Short Term Memory Neural Network<br>
Long short-term memory (LSTM) units are units of a recurrent neural network (RNN). An RNN composed of LSTM units is often called an LSTM network. A common LSTM unit is composed of a cell, an input gate, an output gate and a forget gate. The cell remembers values over arbitrary time intervals and the three gates regulate the flow of information into and out of the cell. LSTM networks are well-suited to classifying, processing and making predictions based on time series data, since there can be lags of unknown duration between important events in a time series. LSTMs were developed to deal with the exploding and vanishing gradient problems that can be encountered when training traditional RNNs. Relative insensitivity to gap length is an advantage of LSTM over RNNs, hidden Markov models and other sequence learning methods in numerous applications.<br>

## Prediction<br>
With the trained models, the predictors load these model and predict answer based on the paragraph context and the question.

