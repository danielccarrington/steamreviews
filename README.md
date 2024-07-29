# Sentiment Analysis of Steam Reviews

Model: [Sentiment Analysis of Steam Reviews.ipynb](<Sentiment Analysis of Steam Reviews.ipynb'>)\
Model Card: [Model Card](<Model Card.md>)\
Data Sheet: [Data Sheet](<Data Sheet.md>)

## Non-Technical Explanation of the Project

The video game store, [Steam](https://store.steampowered.com/), contains a large amount of user submitted reviews for their various games along with a positive or negative score. In this project, we want to apply machine learning to see if we can predict the score based on the review text. If successful, we could then apply this to areas where we don't know if the text has a positive or negative sentiment. For example, classifying posts on a forum, such as [Reddit](https://www.reddit.com/).

## Data

A dataset containing 6.4 million publicly viewable Steam reviews in English. Each row contains the application identifier and name of the game, the review text, the review's score (i.e., positive or negative), and the number of votes the review received. 10,000 rows with a 50/50 split of positive and negative reviews were selected for the model.

Source: [https://www.kaggle.com/datasets/andrewmvd/steam-reviews](https://www.kaggle.com/datasets/andrewmvd/steam-reviews)

![Sample Steam review](images/sample_steam_review.png)\
*A sample Steam review.*

## Model 

The model that is being used is a [convolutional neural network (CNN)](https://en.wikipedia.org/wiki/Convolutional_neural_network) with pretrained weights from [GloVe](https://nlp.stanford.edu/projects/glove/). CNNs, are type of unidirectional neural network that is composed of layers of neurons connected together via weighted paths. However, unlike fully connected networks, the use of filters means that every neuron in a layer is not connected to every other neuron in the prior layer. Instead it is only dependent on the neurons nearby with the number of neurons depending on the filter size, which substantially reduces the number of parameters.

It is one of four common approaches to sentiment analysis including bag-of-words models, recurrent neural networks (RNNs), and transformer models. The model was selected because CNNs can achieve good accuracy in sentiment analysis and are less resource intensive than transformer models.

## Hyperparameter Optimisation

Due to the nature of the project only a small subset of hyperparameters were chosen to be optimised automatically. The hyperparameters that were selected were the batch size, the maximum tokens allowed, and the filter sizes of the convolutional layers. The following options were considered with the only requirement that the batch size had to be greater than the maximum tokens. 

This produced 54 combinations of hyperparameters, which were evaluated using [grid search](https://en.wikipedia.org/wiki/Hyperparameter_optimization#Grid_search) for 15 epochs against the cross entropy loss on the validation set.

Batch Size Options = 256, 512, 1024\
Maximum Token Options = 64, 128, 256, 512\
Filter Size Options = [3, 3], [3, 5], [3, 7], [5, 3], [5, 5], [5, 7]

The top five results by the cross entropy loss on the validation set.

|Batch Size|Max Tokens|Filter Size|Epoch|Training (Loss)    |Training (Accuracy)|Validation (Loss)  |Validation (Accuracy)|Testing (Loss)     |Testing (Accuracy)|
|----------|----------|-----------|-----|-------------------|-------------------|-------------------|---------------------|-------------------|------------------|
|1024      |512       |[3, 7]     |12   |0.2633             |0.8713             |0.4139             |0.7893               |0.4301             |0.7924            |
|512       |256       |[3, 3]     |7    |0.2867             |0.8617             |0.4174             |0.7823               |0.4313             |0.7943            |
|512       |256       |[3, 7]     |7    |0.2943             |0.8567             |0.4192             |0.7830               |0.4317             |0.7942            |
|1024      |512       |[3, 3]     |12   |0.2701             |0.8682             |0.4200             |0.7823               |0.4353             |0.7874            |
|1024      |256       |[3, 7]     |11   |0.2848             |0.8695             |0.4206             |0.7803               |0.4339             |0.7918            |

The entire results can be found here: [grid_search_results.csv](results/grid_search_results.csv)

## Results

After training on the top hyperparameters for 7 epochs, the model managed to achieve a 79.24% accuracy rate in classifying a Steam review as positive or negative. 

The final results can be found here: [final_results.csv](results/final_results.csv)\
Along with the final model checkpoint: [cnn_final.pt](checkpoints/cnn_final.pt)

|Batch Size|Max Tokens|Filter Size|Epoch|Training (Loss)    |Training (Accuracy)|Validation (Loss)  |Validation (Accuracy)|Testing (Loss)     |Testing (Accuracy)|
|----------|----------|-----------|-----|-------------------|-------------------|-------------------|---------------------|-------------------|------------------|
|1024      |512       |[3, 7]     |12   |0.2633             |0.8713             |0.4139             |0.7893               |0.4301             |0.7924            |
