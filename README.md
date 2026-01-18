# 🚀 CryptoAnalyzer - Bitcoin Price Forecasting Platform

A complete Python project for analyzing Bitcoin price data and forecasting future prices using Facebook's Prophet model with a Flask web application.

---

## 📋 Project Overview

This project implements:

- **Data Loading & Preprocessing**: Clean Bitcoin OHLCV data
- **Exploratory Data Analysis**: Visualize price trends and patterns
- **Prophet Time Series Model**: Train and forecast cryptocurrency prices
- **Model Evaluation**: Calculate MAE, RMSE, MAPE, and directional accuracy
- **Flask Web Application**: Interactive dashboard for viewing forecasts
- **Multiple Forecast Horizons**: 7, 30, 60, and 90-day predictions

---

## 🗂️ Project Structure

```
CryptoCurrency/
├── app.py                              # Main Flask application
├── data_loader.py                      # Data loading and preprocessing
├── prophet_model.py                    # Prophet model training
├── model_evaluation.py                 # Model evaluation metrics
├── eda.py                              # Exploratory data analysis
├── requirements.txt                    # Python dependencies
├── README.md                           # This file
├── data/
│   └── bitcoin_2010-07-17_2024-05-23.csv
├── templates/
│   ├── index.html                      # Main dashboard
│   └── about.html                      # About page
├── static/
│   ├── historical.png                  # Historical price plot
│   ├── forecast.png                    # Forecast plot
│   └── evaluation.png                  # Model evaluation
└── model/
    └── prophet_model.pkl               # Saved Prophet model
```

---

## 🚀 Quick Start

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. Prepare Data

Ensure your Bitcoin CSV file is in the project directory. Required columns:

- `Date` - Trading date
- `Open` - Opening price
- `High` - Highest price
- `Low` - Lowest price
- `Close` - Closing price
- `Volume` - Trading volume

### 3. Run the Application

```bash
python app.py
```

The application will:
1. Load and preprocess the data
2. Train the Prophet model
3. Generate evaluation metrics
4. Create visualization plots
5. Start the Flask server

### 4. Access the Web Interface

Open your browser and navigate to:

```
http://localhost:5000
```

---

## 📊 Features

### Dashboard
- 📈 Historical price visualization
- 🔮 Future price forecasts with confidence intervals
- 📊 Model performance metrics (MAE, RMSE, MAPE)
- 💾 Actual vs Predicted price comparison
- 🎛️ Interactive forecast horizon selection (7, 30, 60, 90 days)

### Data Processing
- Automatic datetime parsing
- Missing value handling
- Data validation and cleaning
- Train/test split for evaluation

### Prophet Model
- Automatic trend detection
- Yearly and weekly seasonality
- Changepoint detection
- Uncertainty quantification
- 95% confidence intervals

### Evaluation Metrics
- **MAE**: Mean Absolute Error - Average prediction error
- **RMSE**: Root Mean Squared Error - Penalizes large errors
- **MAPE**: Mean Absolute Percentage Error - Percentage-based accuracy
- **Directional Accuracy**: Percentage of correct up/down predictions

---

## 📁 File Descriptions

### `app.py`

Main Flask application with routes:
- `/` - Home page with dashboard
- `/api/forecast` - JSON API for forecast data
- `/api/metrics` - JSON API for model metrics
- `/about` - Information about the project

### `data_loader.py`

Functions for loading and preprocessing data:
- `load_data()` - Load CSV file
- `preprocess_data()` - Clean and format for Prophet
- `get_train_test_split()` - Split data for evaluation

### `prophet_model.py`

Prophet model training and forecasting:
- `train_prophet_model()` - Train the model
- `create_future_dataframe()` - Create forecast dataframe
- `generate_forecast()` - Generate predictions
- `plot_forecast()` - Visualize forecasts
- `save_model()` / `load_model()` - Model persistence

### `model_evaluation.py`

Model evaluation functions:
- `evaluate_model()` - Calculate evaluation metrics
- `print_evaluation_metrics()` - Display metrics
- `plot_evaluation()` - Plot actual vs predicted

### `eda.py`

Exploratory data analysis:
- `plot_historical_price()` - Historical price chart
- `plot_price_statistics()` - Multi-panel statistics
- `print_data_summary()` - Print summary statistics

---

## 🔧 Configuration

You can modify Prophet model parameters in `prophet_model.py`:

```python
model = Prophet(
    yearly_seasonality=True,        # Include yearly patterns
    weekly_seasonality=True,        # Include weekly patterns
    daily_seasonality=False,        # No daily patterns
    interval_width=0.95,            # 95% confidence interval
    changepoint_prior_scale=0.05    # Changepoint sensitivity
)
```

### Train/Test Split
- **Training data**: All historical data except last 90 days
- **Test data**: Last 90 days of available data
- **Evaluation period**: Full test set

### Seasonality
- **Yearly seasonality**: Captures patterns that repeat annually
- **Weekly seasonality**: Captures patterns that repeat weekly
- **Changepoint detection**: Identifies sudden trend shifts

---

## ⚙️ Dependencies

- **Flask** (2.3.3+) - Web framework
- **Pandas** (2.0.3+) - Data manipulation
- **NumPy** (1.24.3+) - Numerical computing
- **Prophet** (1.1.4+) - Time series forecasting
- **Matplotlib** (3.7.2+) - Data visualization
- **Scikit-learn** (1.3.0+) - Machine learning metrics
- **CmdStanPy** (1.1.0+) - Prophet backend

---

## 🎯 Usage Examples

### Change Forecast Horizon

Click the buttons on the dashboard to select:
- 7 days ahead
- 30 days ahead
- 60 days ahead
- 90 days ahead

### View Model Metrics

The dashboard displays:
- Current Bitcoin price
- Forecasted price at selected horizon
- Predicted percentage change
- Model accuracy metrics
- Confidence interval bounds

### Interpret Plots

1. **Historical Price**: Shows all past price data
2. **Forecast**: Shows predicted prices with uncertainty bands
3. **Evaluation**: Compares actual vs predicted on test data

---

## 📊 Example Output

```
============================================================
DATA SUMMARY
============================================================
Date range: 2010-07-17 00:00:00 to 2024-05-23 00:00:00
Total trading days: 5109

Close Price Statistics:
  Min: $0.05
  Max: $73,750.00
  Mean: $15,423.45
  Median: $8,234.67
  Std Dev: $19,234.56

Volume Statistics:
  Mean: 1234567890
  Max: 9876543210
============================================================

==================================================
MODEL EVALUATION METRICS (TEST SET)
==================================================
Mean Absolute Error (MAE):     $1,234.56
Root Mean Squared Error (RMSE): $1,567.89
Mean Absolute Percentage Error (MAPE): 3.45%
Directional Accuracy:          65.43%
==================================================
```

---

## ⚠️ Important Disclaimer

**This project is for EDUCATIONAL PURPOSES ONLY.**

- Cryptocurrency markets are highly volatile and unpredictable
- Past performance does not guarantee future results
- This model should NOT be used for real financial decisions
- Predictions can be significantly wrong
- Always consult a qualified financial advisor before investing
- Use at your own risk

---

## 🚀 Future Enhancements

- [ ] Support for multiple cryptocurrencies
- [ ] ARIMA and LSTM model comparison
- [ ] Real-time data streaming
- [ ] Sentiment analysis integration
- [ ] User authentication and forecast history
- [ ] REST API for programmatic access
- [ ] Cloud deployment (AWS, Azure, Heroku)
- [ ] Advanced visualization with Plotly
- [ ] Database for historical forecasts
- [ ] Mobile app version

---

## 📚 Resources

- [Facebook Prophet Documentation](https://facebook.github.io/prophet/)
- [Time Series Forecasting](https://en.wikipedia.org/wiki/Time_series)
- [Flask Documentation](https://flask.palletsprojects.com/)
- [Pandas Documentation](https://pandas.pydata.org/)

---

## 📝 License

This project is open source and available for educational use.

---

## 👨‍💻 Author

Created as a comprehensive learning project for time series analysis and forecasting.

---

**Last Updated**: January 2026

For questions or improvements, feel free to enhance and customize this project!
