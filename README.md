================================================================================
HARVEST ATLAS - NASA-Powered Crop-Rotation Decision Support
================================================================================

Harvest Atlas is a local web and terminal decision-support application that 
helps farmers compare crop-rotation scenarios using real NASA agro-climatology, 
global soil data, terrain elevation models, and AI reasoning.

--------------------------------------------------------------------------------
1. SYSTEM REQUIREMENTS & DEPENDENCIES
--------------------------------------------------------------------------------
- Python 3.10 or higher
- Internet connection (to query NASA POWER, OpenLandMap, Open-Meteo, 
  OpenStreetMap Nominatim, and Groq APIs)

Required Python Packages (listed in requirements.txt):
- groq >= 0.9.0
- python-dotenv >= 1.0.0
- flask >= 3.0.0

--------------------------------------------------------------------------------
2. API KEYS & ACCOUNTS
--------------------------------------------------------------------------------
1. Groq API Key (Required for AI scenario generation & plant diagnostics):
   - Create a free account and generate a key at: https://groq.com

2. NASA Earthdata Login (Optional - for MODIS NDVI & SMAP satellite samples):
   - Create a free account at: https://nasa.gov
   - Note: Without this, the app will still function normally and simply report 
     satellite point coverage as a data gap.

--------------------------------------------------------------------------------
3. SETUP PROCEDURE
--------------------------------------------------------------------------------
Step 1: Open your terminal or command prompt and navigate to the project folder.

Step 2: (Recommended) Create and activate a virtual environment:
  - Windows:
      python -m venv .venv
      .venv\Scripts\activate
  - macOS / Linux:
      python3 -m venv .venv
      source .venv/bin/activate

Step 3: Install the required dependencies:
  pip install -r requirements.txt

Step 4: Configure your environment variables:
  Create a file named ".env" in the root project folder (you can copy the 
  provided template file) and add your credentials:

    GROQ_API_KEY=your_groq_key_here

    # Optional: Backup Groq keys (used automatically if primary key hits limits)
    # GROQ_API_KEY_2=your_second_key_here
    # GROQ_API_KEYS=key_one,key_two

    # Optional: Override default AI model (default: openai/gpt-oss-120b)
    # GROQ_MODEL=openai/gpt-oss-20b

    # Optional: NASA AppEEARS satellite samples
    # EARTHDATA_USERNAME=your_earthdata_username
    # EARTHDATA_PASSWORD=your_earthdata_password

  Alternatively, you can set the key directly in your terminal session:
  - Windows PowerShell:  $env:GROQ_API_KEY="your_key_here"
  - Windows CMD:         set GROQ_API_KEY=your_key_here
  - macOS / Linux:       export GROQ_API_KEY="your_key_here"

--------------------------------------------------------------------------------
4. HOW TO RUN THE APPLICATION
--------------------------------------------------------------------------------
Step 1: Start the application from your terminal:
  python main.py

  (If GROQ_API_KEY was not set in .env, the terminal will prompt you to paste it.)

Step 2: Open the Web Interface:
  - Look at the terminal output for the local server URL (by default, this is 
    http://127.0.0.1:5000).
  - Open that URL in your web browser.

Step 3: Use the Decision Lab:
  1. Tap a field on the map or use your browser's GPS location.
  2. Set your farming priorities (0-5 scale) and local soil/irrigation context.
  3. Click "Diagnose this field" to fetch NASA climate, soil, and terrain data, 
     and compare three AI-generated crop-rotation scenarios against your current 
     baseline.

--------------------------------------------------------------------------------
5. TERMINAL CHAT COMMANDS
--------------------------------------------------------------------------------
While the web server runs in the background, you can also chat directly with the 
AI assistant in your terminal window using these commands:

  /help          Show available commands
  /model [name]  View or switch the active Groq model
  /clear         Clear the current terminal conversation history
  /exit          Shut down the server and quit (Ctrl+C also works)

--------------------------------------------------------------------------------
6. DATA SOURCES USED
--------------------------------------------------------------------------------
- NASA POWER (power.larc.nasa.gov) - Daily temperature, rainfall, humidity, 
  wind, solar radiation, and root-zone wetness.
- OpenLandMap SoilDB (openlandmap.org) - Global 0-30 cm soil texture, pH, 
  organic carbon, and bulk density (CC-BY 4.0).
- Copernicus DEM via Open-Meteo - Elevation and terrain slope estimates.
- NASA AppEEARS (appeears.earthdatacloud.nasa.gov) - Optional MODIS NDVI, land-
  surface temperature, and SMAP soil moisture point samples.
- OpenStreetMap Nominatim - Reverse geocoding for location names.
================================================================================
```

<FollowUp>
Would you like me to create a downloadable **README.txt** file for you, or adjust any sections to include **project folder structure** and **troubleshooting tips**?
</FollowUp>
