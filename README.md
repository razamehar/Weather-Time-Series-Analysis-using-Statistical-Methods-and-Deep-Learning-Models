# Weather Time Series Analysis using Statistical Methods and Deep Learning Models

## Project Overview
In this project, a diverse array of statistical methods and deep learning models were explored for the multi-variate time series analysis. Techniques such as Naive Forecasting, Moving Average Forecasting, Differenced Moving Average Forecasting, and Differenced Moving Average Forecasting with Smoothing were meticulously examined. Within the realm of deep learning, Simple Neural Networks, Deep Neural Networks, Single-Layer LSTMs, Single-Layer Regularized LSTMs, Bi-Directional Regularized LSTMs, Regularized Stacked GRUs, and Convolutional Layers with Stacked GRUs and Fully Connected Layers were analyzed. Through rigorous comparison and evaluation, the most effective methodology for achieving accurate and reliable weather predictions were sought. This involved establishing baseline, selecting the best model using learning rate scheduler, and conducting performance comparisons against baseline.

##  Statistical Analysis of Variables

### Univariate Analysis
In this phase, individual variables are analyzed to understand their distribution and normality. Utilizing histograms and quantile-quantile (qq) plots, we gain insights into their characteristics.

<table>
  <tr>
    <td style="text-align: center;">
      <div>Histograms</div>
      <img src="docs/1uni.png" alt="histograms" style="max-width: 100%;">
    </td>
    <td style="text-align: center;">
      <div>Quantile-Quantile Plots</div>
      <img src="docs/2qq.png" alt="qq-plots" style="max-width: 100%;">
    </td>
  </tr>
</table>

### Correlation Analysis
Exploring relationships between variables, correlation analysis employs Pearson correlation coefficients. A correlation matrix visualized through a heatmap highlights the strengths of correlations with 'T (degC)', offering valuable insights into inter-variable relationships and dependencies.

<table>
  <tr>
    <td style="text-align: center;">
      <div>Heatmap of Correlation Coefficients</div>
      <img src="docs/3corr.png" alt="heatmap" style="max-width: 100%;">
    </td>
  </tr>
</table>
      
## Data Visualization
Time series plots depict temperature variations over time, revealing both long-term trends and short-term fluctuations within seasonal cycles. Annual temperature trend analysis showcases maximum, average, and minimum temperatures annually, aiding in the interpretation of climate data and identification of seasonal patterns.

<table>
  <tr>
    <td style="text-align: center;">
      <div>Seasonality</div>
      <img src="docs/4season.png" alt="seasonality" style="max-width: 100%;">
    </td>
    <td style="text-align: center;">
      <div>Seasonality without Noise</div>
      <img src="docs/5season.png" alt="seasonality without noise" style="max-width: 100%;">
    </td>
     <td style="text-align: center;">
      <div>Seasonality (First Season Cycle)</div>
      <img src="docs/6seaons.png" alt="first season cycle" style="max-width: 100%;">
    </td>
     <td style="text-align: center;">
      <div>Temperature over the Years</div>
      <img src="docs/7temp.png" alt="temperature over the years" style="max-width: 100%;">
    </td>
  </tr>
</table>

## Statistical Forecast Methods

### Fixed Partitioning for Statistical Methods based Forecasting
A systematic partitioning approach divides temperature data into training and testing sets. Data from 2012 to 2014 are allocated for training to enable model learning from historical data, while data from subsequent years are reserved for validation and testing, ensuring accurate predictions of future temperatures.

### Naive Forecast
Predictions are based solely on the last observed temperature, serving as a baseline for accuracy assessment.

<table>
  <tr>
    <td style="text-align: center;">
      <div></div>
      <img src="docs/8nf.png" alt="naive forecast" style="max-width: 100%;">
    </td>
  </tr>
</table>

### Moving Average Forecasting
Average temperatures over defined window sizes are computed to smooth short-term fluctuations and highlight long-term trends.

<table>
  <tr>
    <td style="text-align: center;">
      <div></div>
      <img src="docs/9ma.png" alt="moving average" style="max-width: 100%;">
    </td>
  </tr>
</table>

### Differenced Moving Average Forecast
By differencing to remove trends and seasonality before applying a moving average, this method refines predictions and improves accuracy.

<table>
  <tr>
    <td style="text-align: center;">
      <div></div>
      <img src="docs/10difmv.png" alt="Differenced Moving Average" style="max-width: 100%;">
    </td>
  </tr>
</table>

### Differenced Moving Average Forecast with Trend & Seasonality Added
Seasonality and Trend added back to the differenced moving average.

<table>
  <tr>
    <td style="text-align: center;">
      <div></div>
      <img src="docs/11difmv.png" alt="Differenced Moving Average with Trend & Seasonality Added" style="max-width: 100%;">
    </td>
  </tr>
</table>

### Differenced Moving Average Forecast with Smoothing
Using centered approach to smooth the data at each step. For instance, to smooth the data point at t = 365, we would compute the average of the values from t = 359 to t = 370, with the window size of 11.

<table>
  <tr>
    <td style="text-align: center;">
      <div></div>
      <img src="docs/12diffmv.png" alt="Differenced Moving Average with Smoothing" style="max-width: 100%;">
    </td>
  </tr>
</table>

## Deep Learning Models
Various deep learning models, including Basic Neural Network, Deep Neural Network, LSTM, Regularized LSTM, Bi-Directional LSTM, Stacked GRUs, and Convolutional layer with stacked GRUs and Fully Connected Layers are explored for temperature forecasting, each tailored to leverage sequential data characteristics for enhanced prediction accuracy.

### Fixed Partitioning for Neural Network based Forecasting
Temperature data are split into training, validation, and testing sets ensuring chronological order and accounting for seasonality, essential for effective model training and evaluation.

### Data Preprocessing
Data normalization using MinMaxScaler ensures consistent scaling, particularly beneficial for non-normally distributed data and when training neural networks with features of different scales.

### Sequence Generation
Sequences are generated from input array data using TensorFlow's timeseries_dataset_from_array, facilitating training, validation, and testing of models with specified sequence lengths.

### Model Finalization
The two most promising models, determined by their low loss and Mean Absolute Error (MAE), were selected for further refinement. They underwent fine-tuning using a learning rate schedule to identify the optimal learning rate and were then retrained on the dataset. Among these models, the one exhibiting the best performance with the new learning rate was chosen as the final selection.

<table>
  <tr>
    <td style="text-align: center;">
      <div>Training Loss versus Learning Rate for Model 1</div>
      <img src="docs/lr_1.png" alt="Training Loss versus Learning Rate for Model 1" style="max-width: 100%;">
    </td>
    <td style="text-align: center;">
      <div>Training Loss versus Learning Rate for Model 2</div>
      <img src="docs/lr_2.png" alt="Training Loss versus Learning Rate for Model 2" style="max-width: 100%;">
    </td>
  </tr>
</table>

### Evaluation
Model performance is evaluated using Mean Absolute Error (MAE) metric on the test dataset, comparing predictions against actual values to quantify forecasting accuracy.

## Weather Forecast
Trained models are utilized to predict future temperature values, leveraging the learned patterns and dependencies in the data to provide accurate forecasts.

## Potential Improvements
- Adjust the number of units.
- Experiment with different learning rates and batch sizes.

## Data Sources:
https://s3.amazonaws.com/keras-datasets/jena_climate_2009_2016.csv.zip

## License:
This project is licensed under the Raza Mehar License. See the LICENSE.md file for details.

## Contact:
For any questions or clarifications, please contact Raza Mehar at [raza.mehar@gmail.com].
