# Spectral Temporal Graph Neural Network for Multivariate Time-series Forecasting

This repository is the official implementation of Spectral Temporal Graph Neural Network for
Multivariate Time-series Forecasting.

# The predicted results of the RH column
![RH column][RH]
# The predicted results of the Barometer column
![RH column][Barometer]
...
# Note:
This is only an application in a course exercise. You can view the original source code of the article "Spectral Temporal Graph Neural Network for Multivariate Time-series Forecasting" at https://github.com/microsoft/StemGNN.

## Requirements

```setup
python3.7 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

## Datasets

The input csv file should contain **no header** and its **shape should be `T*N`**, where `T` denotes total number of timestamps, `N` denotes number of nodes.

## Training and Evaluation

The training procedure and evaluation procedure are all included in the `main.py`. To train and evaluate on some dataset, run the following command:

```train & evaluate
python main.py --train True --evaluate True --dataset <name of csv file> --output_dir <path to output directory> --n_route <number of nodes> --window_size <length of sliding window> --horizon <predict horizon> --norm_method z_score --train_length 7 --validate_length 2 --test_length 1
```

The detailed descriptions about the parameters are as following:

| Parameter name | Description of parameter |
| --- | --- |
| train | whether to enable training, default True |
| evaluate | whether to enable evaluation, default True |
| dataset | file name of input csv |
| window_size | length of sliding window, default 12 |
| horizon | predict horizon, default 3 |
| train_length | length of training data, default 24 |
| validate_length | length of validation data, default 2 |
| test_length | length of testing data, default 1 |
| epoch | epoch size during training, default 100 |
| lr | learning rate, default 1e-4 |
| multi_layer | hyper parameter of STemGNN which controls the parameter number of hidden layers, default 5 |
| device | device that the code works on, 'cpu' or 'cuda:x' | 
| validate_freq | frequency of validation, default 1 |
| batch_size | batch size, default 32 |
| norm_method | method for normalization, 'z_score' or 'min_max' |
| early_stop | whether to enable early stop, default False |


## Results

| Dataset | MAE  | RMSE | MAPE |
| -----   | ---- | ---- | ---- |
| 17 columns | 19.21 | 45.9448| 0.13|

[RH]: RH_column.png
[Barometer]: Barometer_column.png