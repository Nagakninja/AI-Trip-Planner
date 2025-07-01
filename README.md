# AI Trip Planner

AI Trip Planner is an intelligent travel planning assistant that generates detailed, well-formatted travel itineraries using advanced AI models. The application exports travel plans as Markdown files, making it easy to share, print, or further customize your trip details.

## Features

- **AI-Generated Travel Plans:** Get personalized, day-by-day itineraries for your trips.
- **Markdown Export:** Save your travel plan as a Markdown file with metadata and helpful notes.
- **Automatic Output Directory Handling:** The app creates an output folder if it doesn't exist.
- **Timestamped Files:** Each plan is saved with a unique timestamp for easy organization.
- **FastAPI Backend:** Provides a REST API for generating travel plans and visualizing the agentic workflow graph.
- **Streamlit Frontend:** User-friendly chat interface for planning trips interactively.
- **Integrated Tools:** Weather info, place search, expense calculator, and currency conversion tools.

## How It Works

1. The user provides a travel query or request via the Streamlit app or API.
2. The AI agent generates a detailed travel plan, using integrated tools as needed.
3. The plan is saved as a Markdown file in the `output` directory, with metadata such as generation time and author.

## Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone <your-repo-url>
   cd AI-Trip-Planner
   ```

2. **Install Dependencies**
   Make sure you have Python 3.8+ installed. Then run:
   ```bash
   pip install -r requirements.txt
   ```

3. **Set Up Environment Variables**
   Create a `.env` file in the project root with your API keys:
   ```env
   OPENWEATHERMAP_API_KEY=your_openweathermap_key
   GPLACES_API_KEY=your_google_places_key
   TAVILY_API_KEY=your_tavily_key
   # Add other keys as needed
   ```

4. **Run the Backend (FastAPI)**
   ```bash
   uvicorn main:app --reload
   ```
   The API will be available at `http://localhost:8000`.

5. **Run the Frontend (Streamlit)**
   ```bash
   streamlit run streamlit_app.py
   ```
   Access the app at `http://localhost:8501`.

## Example Usage

```python
from utils.save_to_document import save_document

response_text = "Your AI-generated travel plan here..."
save_document(response_text)
```

This will create a file like `output/AI_Trip_Planner_2025-07-01_15-30-00.md` with your travel plan.

## File Structure

```
AI-Trip-Planner/
├── main.py                # FastAPI backend
├── streamlit_app.py       # Streamlit frontend
├── utils/
│   ├── save_to_document.py
│   ├── expense_calculator.py
│   ├── currency_converter.py
│   ├── weather_info.py
│   └── ...
├── tools/
│   ├── weather_info_tool.py
│   ├── place_search_tool.py
│   ├── expense_calculator_tool.py
│   ├── currency_conversion_tool.py
│   └── ...
├── prompt_library/
│   └── prompt.py
├── output/
│   └── AI_Trip_Planner_<timestamp>.md
├── requirements.txt
├── .env
└── ...
```

## Available Tools

- **Weather Info Tool:** Fetches current weather and forecasts for any city.
- **Place Search Tool:** Finds attractions and restaurants using Google Places and Tavily.
- **Expense Calculator Tool:** Helps estimate and split travel expenses.
- **Currency Conversion Tool:** Converts currencies for international trips.

## Notes

- The output Markdown file includes a disclaimer to verify all information before your trip.
- The output directory and file naming are handled automatically for convenience and organization.
- Make sure to set up all required API keys in your `.env` file for full functionality.

## License

This project is licensed under the MIT License.
