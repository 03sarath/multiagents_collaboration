
🌆 Smart City Assistant (Multi-Agent System)

A LangGraph-powered assistant that provides event, weather, and restaurant recommendations for any city using Mistral (free tier), Cohere, Tavily, and OpenWeatherMap APIs.

---

📋 Prerequisites

- Python 3.9+
- Poetry (recommended) or pip
- API keys for:
  - Mistral
  - Cohere
  - Tavily
  - OpenWeatherMap

---

🚀 Setup Guide

1. Clone the Repository

2. Set Up Virtual Environment

Option A: Using Poetry
    poetry install
    poetry shell

Option B: Using pip and venv
    python -m venv venv
    source venv/bin/activate      # Linux/macOS
    venv\Scripts\activate       # Windows
    pip install -r requirements.txt

3. Install Core & Dev Dependencies (if using Poetry)
    poetry add langgraph cohere tavily-python pyowm faiss-cpu python-dotenv
    poetry add --group dev jupyter ipython

4. Configure Environment Variables
Create a .env file:
    MISTRAL_API_KEY=your_mistral_key
    COHERE_API_KEY=your_cohere_key
    TAVILY_API_KEY=your_tavily_key
    OPENWEATHERMAP_API_KEY=your_weather_key

5. Prepare the Local SQLite Database
    python -c "
    import sqlite3
    conn = sqlite3.connect('local_info.db')
    conn.execute('''
        CREATE TABLE IF NOT EXISTS local_events (
            event_name TEXT,
            event_date TEXT,
            description TEXT,
            city TEXT
        )
    ''')
    conn.commit()
    "

---

🏗️ Project Structure

.
├── agents/
│   ├── events.py
│   ├── weather.py
│   ├── restaurants.py
│   └── analysis.py
├── tools/
│   ├── search.py
│   └── weather.py
├── graph.py
├── app.py
├── data/
├── Smart_City_Assistant.ipynb
├── .env
└── README.md

---

🖥️ Running the System

Option 1: Jupyter Notebook
    jupyter Notebook

Option 2: Command Line
    python app.py --city "Tampa"

✅ Expected Output
    ✅ Found 3 events in Tampa:
    - Jazz Festival (Nov 15)
    - Art Walk (Nov 20)

    🌤️ Weather: Sunny, 28°C

    🍽️ Top Restaurants:
    1. Columbia Restaurant (4.6⭐)
    2. Bern's Steakhouse (4.8⭐)

---

🔧 Troubleshooting

API Errors:
- Check your .env file
- Monitor API rate limits

Database Issues:
    rm local_info.db

Missing Dependencies:
    poetry install --sync
    or
    pip install -r requirements.txt

---

📦 requirements.txt

langgraph>=0.0.30
cohere>=4.0.0
tavily-python>=0.0.3
pyowm>=3.3.0
faiss-cpu>=1.7.4
python-dotenv>=1.0.0

---

📜 License

MIT License

---

🙏 Acknowledgments

- Mistral AI
- LangChain
- Cohere
- Tavily
- OpenWeatherMap

---

🌟 Key Features

- Modular Agents
- LangGraph Integration
- Multi-API Fusion
- Flexible Setup
- Built-in Troubleshooting

---

