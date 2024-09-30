# Artificial neural network for time series forecasting

*Developed between November and December 2023 at Politecnico di Milano*

The goal of the project is to design and implement forecasting models to learn how to exploit past observations in the input sequences to correctly predict the future. The task is to develop a forecasting model that is able to predict several uncorrelated time series. The prerequisite is that the model exhibits generalisation capabilities in the forecasting domain, allowing it to transcend the constraints of specific time domains. This requires a model that, while specialised in forecasting, is not limited to predicting in a single or predefined time context.
The model learns from a set of possible categories time series. **Attention model** with **Transformer arichitecture** turns out to be the best

## Project stucture and models
Have a look at the [report](https://github.com/lorenzofranze/ANN-time-series-forecasting/blob/main/report.pdf) to see the result of the analysis.
All the models have been uploaded and they were used to conduct different experiments for our task. 

We built an ensemble model where we trained different models for each of the different classes in the dataset and two general models trained on the whole dataset, one that used **bidirectional LSTM** and a **seq2seq** model that also included an incorporated **attention mechanism**.

### Methodology
- Data exploration and preprocessing
- Models
  - Models based on category splitting
  - Pure biLSTM approach: this model includes a bidirectional LSTM with 2 convolutional layers and a final cropping layer
  - Seq2seq approach:  seq2seq architecture with an incorporated attention mechanism, the architecture comprised an encoder LSTM, passing its final state to a decoder LSTM as repeated input.
- Evaluations on test set

## Dataset Structure

[Link to the dataset](https://drive.google.com/drive/u/0/folders/1127Igo4_-CgMiVyRzG5aCiKEq0z9Kiwa)

Dataset Details:
* Time series length: the length of the time series in the training dataset is variable. To simplify the portability of the dataset, we padded with zeros the sequences to the maximum length of 2776. Thus, the dataset is provided in a compact form as a Nx2776 array. We provide an additional 'valid_periods.npy' file containing the information to recover the original time series without the padding.
* File Format: npy
* Categories: the provided time series are composed by sequences collected from 6 different sources. We further provide additional information about the category of each time series.

Single folder containing the following files:
* 'training_data.npy': it contains a numpy array of shape (48000, 2776). 48000 time series of length 2776.
* 'valid_periods.npy': it contains a numpy array of type (48000, 2) containing for each of the time series the start and end index of the current series, i.e. the part without padding.
* 'categories.npy': it contains a numpy array of shape (48000,), containing for each of the time series the code of its category. The possible categories are in {'A', 'B', 'C', 'D', 'E', 'F'}.

IMPORTANT: This is a dataset consisting of monovariate time series, i.e. composed of a single feature, belonging to six different domains. The time series of each domain are not to be understood as closely related to each other, but only as collected from similar data sources.
What is required is therefore to build a model that is capable of generalising sufficiently to predict the future samples of the 60 time series of the test set.









