# ⚡ ThunderCast: Smart Storm Prediction Engine

**Real-time Thunderstorm Prediction System using Time-Series Forecasting**

---

## 📋 Project Overview

ThunderCast is an automated thunderstorm prediction system that uses Facebook Prophet (time-series forecasting) to predict thunderstorm probabilities for Pimpri-Chinchwad, Pune. The system collects real-time weather data, analyzes patterns, and provides predictions with an interactive dashboard.

---

## 🎯 Features

- ✅ **Real-time Weather Data Collection** - Automated hourly data collection via OpenWeatherMap API
- ✅ **Time-Series Forecasting** - Facebook Prophet model for thunderstorm prediction
- ✅ **Interactive Dashboard** - Built with Streamlit and Plotly for data visualization
- ✅ **Historical Analysis** - EDA and statistical insights on 13+ years of weather data
- ✅ **Automated Predictions** - 6-24 hour thunderstorm probability forecasts
- ✅ **Cloud Database** - Supabase for data storage and retrieval

---

## 🛠️ Tech Stack

**Languages & Libraries:**
- Python 3.13
- Pandas & NumPy (Data manipulation)
- Prophet (Time-series forecasting)
- Plotly (Interactive visualizations)
- Streamlit (Dashboard framework)

**Tools & Services:**
- Supabase (PostgreSQL database)
- OpenWeatherMap API (Weather data source)
- APScheduler (Task automation)

**Domain:**
- Time-Series Forecasting
- Weather Analytics
- Predictive Analytics

---

## 📂 Project Structure
```
ThunderCast/
│
├── data/
│   ├── raw/              # Raw Kaggle dataset
│   ├── processed/        # Cleaned and featured data
│   ├── models/           # Trained Prophet model
│   └── visualizations/   # Generated charts (Plotly HTML files)
│
├── src/
│   ├── data_collection.py      # Fetch weather data from API
│   ├── data_exploration.py     # Initial data exploration
│   ├── data_cleaning.py        # Data cleaning and preprocessing
│   ├── eda_analysis.py         # Exploratory Data Analysis
│   ├── feature_engineering.py  # Feature creation
│   ├── model_training.py       # Prophet model training
│   ├── prediction.py           # Generate predictions
│   ├── scheduler.py            # Automated data collection
│   └── visualizations.py       # Create Plotly charts
│
├── dashboard/
│   └── app.py            # Streamlit dashboard
│
├── config/
│   └── config.py         # Configuration settings
│
├── .env                  # Environment variables (API keys)
├── requirements.txt      # Python dependencies
└── README.md            # Project documentation
```

---

## 🚀 Installation & Setup

### Prerequisites
- Python 3.13+
- pip package manager
- Supabase account (free tier)
- OpenWeatherMap API key (free)

### Step 1: Clone Repository
```bash
git clone <repository-url>
cd ThunderCast
```

### Step 2: Create Virtual Environment
```bash
python -m venv venv
venv\Scripts\activate  # Windows
# source venv/bin/activate  # Mac/Linux
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Configure Environment Variables
Create `.env` file in project root:
```
SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_anon_key
OPENWEATHER_API_KEY=your_openweather_api_key
```

### Step 5: Setup Database
Run SQL script in Supabase SQL Editor to create tables:
```sql
-- weather_data table
CREATE TABLE weather_data (
    id BIGSERIAL PRIMARY KEY,
    timestamp TIMESTAMPTZ DEFAULT NOW(),
    temperature FLOAT,
    humidity FLOAT,
    pressure FLOAT,
    wind_speed FLOAT,
    cloud_cover FLOAT,
    location VARCHAR(100),
    latitude FLOAT,
    longitude FLOAT
);

-- predictions table
CREATE TABLE predictions (
    id BIGSERIAL PRIMARY KEY,
    prediction_time TIMESTAMPTZ DEFAULT NOW(),
    forecast_time TIMESTAMPTZ,
    thunderstorm_probability FLOAT,
    location VARCHAR(100),
    model_version VARCHAR(50)
);

-- alerts table (optional)
CREATE TABLE alerts (
    id BIGSERIAL PRIMARY KEY,
    alert_time TIMESTAMPTZ DEFAULT NOW(),
    location VARCHAR(100),
    severity VARCHAR(20),
    message TEXT,
    sent BOOLEAN DEFAULT FALSE
);
```

---

## 📊 Usage

### 1. Collect Weather Data
```bash
python src/data_collection.py
```

### 2. Data Cleaning & Feature Engineering
```bash
python src/data_cleaning.py
python src/feature_engineering.py
```

### 3. Train Model
```bash
python src/model_training.py
```

### 4. Generate Predictions
```bash
python src/prediction.py
```

### 5. Launch Dashboard
```bash
streamlit run dashboard/app.py
```

### 6. Run Automated Scheduler (Optional)
```bash
python src/scheduler.py
```

---

## 📈 Model Details

**Algorithm:** Facebook Prophet (Time-Series Forecasting)

**Features Used:**
- Temperature (°C)
- Humidity (%)
- Atmospheric Pressure (hPa)
- Wind Speed (km/h)
- Cloud Cover (%)
- Precipitation (mm)

**Target Variable:** Thunderstorm occurrence (Binary: 0/1)

**Training Data:** 116,135 hourly records (2008-2022, Pune weather)

**Prediction Horizon:** 6-24 hours ahead

**Performance Metrics:**
- Model captures seasonal patterns
- Identifies high-risk conditions (humidity >70%, pressure <1010 hPa)
- Low false positive rate for clear weather conditions

---

## 🎨 Dashboard Features

**Live Weather Monitoring:**
- Current temperature, humidity, pressure, wind speed, cloud cover

**Thunderstorm Predictions:**
- 6-24 hour probability forecast
- Risk level indicators (Low/Moderate/High)
- Interactive Plotly charts

**Historical Trends:**
- Multi-parameter weather visualizations
- Statistical summaries
- Customizable time ranges (6h, 12h, 24h, 7 days)

---

## 🔑 Key Insights from EDA

1. **Thunderstorm Conditions:**
   - Average humidity during storms: 85%+
   - Average pressure during storms: <1008 hPa
   - Peak occurrence: Monsoon season (June-September)

2. **Temporal Patterns:**
   - Higher frequency in afternoon/evening hours
   - Seasonal variations clearly visible

3. **Data Quality:**
   - 0% missing values
   - 116,136 complete records
   - 482 thunderstorm events identified (0.42%)

---

## 🎯 Future Enhancements

- [ ] Add multiple location support
- [ ] Implement SMS/Email alert system
- [ ] Mobile app development
- [ ] Integration with disaster management systems
- [ ] Real-time model retraining pipeline
- [ ] Advanced ML models (LSTM, XGBoost comparison)

---

## 👨‍💻 Author

**[Your Name]**
- Final Year Project
- Data Analytics Student
- [LinkedIn](your-linkedin) | [GitHub](your-github)

---

## 📝 License

This project is for educational purposes.

---

## 🙏 Acknowledgments

- OpenWeatherMap for weather data API
- Facebook (Meta) for Prophet library
- Supabase for cloud database
- Kaggle for historical weather dataset

---

## 📞 Contact

For queries or collaboration:
- Email: your.email@example.com
- LinkedIn: [Your Profile]

---

**Built with ❤️ using Python, Prophet, and Streamlit**"# ThunderCast-Smart-Storm-Prediction-Engine" 
