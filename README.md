# Weather Agent Demo

## Project Overview

This project is one of my **Capstone Project**  with the **National University of Singapore (NUS)** to demonstrate the application of techniques for effective communication and coordination among multiple agents using AI-powered function calling.

The Weather Agent is an intelligent system that uses OpenAI's GPT-4 model with function calling capabilities to understand natural language queries about weather and retrieve real-time weather information from WeatherAPI.com. This simple agent showcases how AI agents can effectively communicate, coordinate, and integrate with external APIs to fulfill user requests.

## Key Learning Objectives

- Apply techniques for effective communication and coordination among multiple agents
- Demonstrate AI function calling capabilities for seamless agent interaction
- Integrate external APIs with LLM-powered agents
- Implement error handling and user-friendly responses in multi-agent systems

## Technologies Used

### Core Technologies
- **Python 3.x** - Primary programming language
- **OpenAI API (GPT-4)** - Large Language Model with function calling capabilities
- **WeatherAPI.com** - Real-time weather data provider
- **Jupyter Notebook** - Interactive development environment

### Python Libraries
- **openai (v0.28)** - OpenAI API client for GPT-4 integration
- **requests** - HTTP library for making API calls to WeatherAPI
- **python-dotenv** - Environment variable management
- **json** - JSON parsing and manipulation
- **google.colab.userdata** - Secure API key management (for Google Colab environment)

## Features

### 1. Natural Language Understanding
The agent can interpret various weather-related queries in natural language:
- "What's the weather like in Singapore?"
- "Is it raining in London right now?"
- "Tell me the temperature in New York"
- "How hot is the weather tonight in Sydney?"

### 2. Function Calling Integration
Demonstrates OpenAI's function calling feature where:
- GPT-4 intelligently determines when to call the `get_weather` function
- Extracts location parameters from user queries
- Coordinates between the AI model and external weather API

### 3. Rich Weather Information
Provides comprehensive weather data including:
- 🌡️ Current temperature and "feels like" temperature
- ☁️ Weather condition with appropriate emoji
- 💨 Wind speed and direction
- 💧 Humidity levels
- 🕐 Last updated timestamp

### 4. Error Handling
Robust error handling for:
- Invalid city names
- API connection issues
- Malformed requests

## Setup Instructions

### Prerequisites
- Python 3.7 or higher
- OpenAI API account and API key
- WeatherAPI.com account and API key
- Google Colab account (if running in Colab) or local Jupyter environment

### Installation

1. **Clone or download this repository**

2. **Install required dependencies**
   ```bash
   pip install openai==0.28 requests python-dotenv
   ```

3. **Configure environment variables**
   - Copy `.env.sample` to `.env`
   - Add your API keys to the `.env` file:
     ```
     OPENAI_API_KEY=your_openai_api_key_here
     WEATHER_API_KEY=your_weather_api_key_here
     ```

4. **Get API Keys**
   - **OpenAI API Key**: Sign up at [https://platform.openai.com](https://platform.openai.com)
   - **WeatherAPI Key**: Sign up at [https://www.weatherapi.com](https://www.weatherapi.com)

### Running the Project

#### In Google Colab:
1. Upload `weather_agent.ipynb` to Google Colab
2. Store your API keys in Colab's userdata:
   - Go to Secrets (🔑) in the left sidebar
   - Add `OPENAI_NEW` with your OpenAI API key
   - Add `WEATHER_API_KEY` with your WeatherAPI key
3. Run all cells sequentially

#### In Local Jupyter:
1. Open `weather_agent.ipynb` in Jupyter Notebook or JupyterLab
2. Modify the code to use `python-dotenv` instead of `google.colab.userdata`:
   ```python
   from dotenv import load_dotenv
   import os
   
   load_dotenv()
   openai.api_key = os.getenv('OPENAI_API_KEY')
   weather_api_key = os.getenv('WEATHER_API_KEY')
   ```
3. Run all cells sequentially

## Project Structure

```
openai_weather_agent_demo/
├── weather_agent.ipynb    # Main Jupyter notebook with all implementation
├── README.md              # Project documentation (this file)
└── .env.sample            # Sample environment variables file
```

## How It Works

### 1. Weather API Integration
The `get_weather()` function retrieves current weather data from WeatherAPI.com for any given location.

### 2. OpenAI Function Definition
The agent defines a function schema that GPT-4 can understand and call when needed:
```python
{
    "name": "get_weather",
    "description": "Get current weather for a location",
    "parameters": {
        "type": "object",
        "properties": {
            "location": {
                "type": "string",
                "description": "City name or location"
            }
        },
        "required": ["location"]
    }
}
```

### 3. Agent Coordination
The `weather_agent()` function coordinates between:
- User input (natural language query)
- GPT-4 (understanding intent and extracting location)
- Weather API (fetching real-time data)
- Response formatting (presenting information with emojis)

### 4. Multi-Agent Communication
This project demonstrates effective agent communication by:
- **User Agent** → **AI Agent**: Natural language query
- **AI Agent** → **Function Agent**: Structured function call with parameters
- **Function Agent** → **External API**: HTTP request for data
- **External API** → **Function Agent**: JSON weather data
- **Function Agent** → **AI Agent**: Processed data
- **AI Agent** → **User Agent**: Formatted, human-readable response

## Example Usage

```python
# Query the weather agent
query = "What's the weather like in Singapore?"
response = weather_agent(query)
print(response)

# Output:
# ☁️ Current weather in Singapore at 2026-01-16 14:30:
#   Temperature: 28.0°C (feels like 32.0°C)
#   Condition: Partly cloudy
#   Wind: 15.5 kph NE
#   Humidity: 75%
```

## Capstone Project Context

This project was developed as part of a capstone course at the **National University of Singapore (NUS)** focusing on:

- **Multi-Agent Systems**: Understanding how different agents (LLM, API, function handlers) communicate and coordinate
- **Natural Language Processing**: Leveraging GPT-4's language understanding capabilities
- **API Integration**: Connecting AI systems with real-world data sources
- **Error Handling**: Building robust systems that gracefully handle failures
- **User Experience**: Designing intuitive interfaces with rich, formatted outputs

## Future Enhancements

- Add support for weather forecasts (3-day, 7-day)
- Implement multi-location comparison
- Add weather alerts and warnings
- Support for different units (Imperial/Metric)
- Historical weather data queries
- Integration with additional weather data providers

## License

This project is for educational purposes as part of the NUS capstone program.

## Acknowledgments

- **National University of Singapore (NUS)** for providing the learning framework and project guidance
- **OpenAI** for GPT-4 and function calling capabilities
- **WeatherAPI.com** for real-time weather data


**Note**: This is an educational project demonstrating multi-agent communication and coordination techniques. API keys should be kept secure and never committed to version control.
