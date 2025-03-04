# Screenpipe Parental Control Dashboard

A comprehensive monitoring system that tracks children's screen time, analyzes content for appropriateness, and provides real-time alerts to parents.

## Overview

This application combines real-time screen monitoring (via Screenpipe), content analysis (via Llama/Gemini AI), and a user-friendly dashboard to help parents monitor their children's digital activities. The system captures screen content, analyzes it for age-appropriateness, tracks usage patterns, and generates alerts for potentially concerning content or excessive screen time.

## Features

- **Real-time Screen Monitoring**: Captures current app usage and screen content
- **Content Analysis**: Uses AI to analyze screen content for age-appropriateness
- **Usage Tracking**: Monitors screen time and app usage patterns
- **Alert System**: Generates alerts for inappropriate content or excessive usage
- **User-friendly Dashboard**: Displays children's activities, screen time, and alerts
- **Multiple Children Support**: Tracks and displays data for multiple children

## System Architecture

The application consists of several components:

1. **Backend Modules**:
   - `screenpipe_connector.py`: Interfaces with the Screenpipe API to capture screen content
   - `llama_client.py`: Connects to Llama/Gemini AI for content analysis
   - `query_engine.py`: Processes and structures queries to the AI
   - `config.py`: Contains configuration settings

2. **Database**:
   - SQLite database storing children's information, app usage, OCR data, and alerts

3. **Dashboard**:
   - Flask web application serving the frontend
   - API endpoints for retrieving and updating data
   - HTML/CSS/JavaScript frontend for displaying the dashboard

4. **Data Collection**:
   - `update_alex_data.py`: Script to collect and analyze real-time data

## File Structure

```
ScreenPipe_Visionify/
├── App/
│   ├── screenpipe_connector.py  # Connects to Screenpipe for screen monitoring
│   ├── llama_client.py          # Interfaces with Gemini
│   ├── query_engine.py          # Processes AI queries
│   ├── main.py                  # Main application logic
│   └── config.py                # Configuration settings
├── Dashboard/
│   └── data/
│       └── database.db          # SQLite database
├── frontend/
│   ├── index.html               # Dashboard HTML
│   ├── css/
│   │   └── styles.css           # Dashboard styling
│   └── js/
│       └── dashboard.js         # Dashboard functionality
├── database_app.py              # Flask application serving the dashboard
└── update_alex_data.py          # Script to update data from Screenpipe and Gemini
```

## Setup and Installation

### Prerequisites

- Python 3.8 or higher
- Screenpipe API access
- Gemini API key (or other AI service)
- SQLite

### Installation Steps

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/ScreenPipe_Visionify.git
   cd ScreenPipe_Visionify
   ```

2. **Install dependencies**:
   ```bash
   pip install flask requests google-generativeai sqlite3
   ```

3. **Set up environment variables**:
   ```bash
   export GEMINI_API_KEY="MY_API"
   ```

4. **Initialize the database**:
   ```bash
   python3 update_alex_data.py --init
   ```

## Usage

### Running the Dashboard

1. **Start the Flask application**:
   ```bash
   python3 database_app.py
   ```

2. **Access the dashboard**:
   Open your browser and navigate to `http://localhost:5000/`

### Updating Data

To update the dashboard with real-time data:

```bash
python3 update_alex_data.py
```

For continuous monitoring:

```bash
python3 update_alex_data.py --continuous --interval 300
```

This will update the data every 5 minutes (300 seconds).

To update data for all children:

```bash
python3 update_alex_data.py --all
```

## Dashboard Features

### Summary Section
- Total screen time today
- Productive screen time
- Number of active alerts

### Children Section
- List of all children with their current status
- Current app and session information
- Device type and age

### Alerts Section
- List of active alerts with severity levels
- Alert details including app name and timestamp
- Option to resolve alerts

## Database Schema

The application uses an SQLite database with the following tables:

- **children**: Stores information about each child
- **app_usage**: Tracks app usage sessions
- **ocr_data**: Stores OCR text extracted from screens
- **app_analysis**: Contains analysis results for apps
- **alerts**: Stores alerts generated by the system
- **current_sessions**: Tracks currently active sessions

## API Endpoints

The Flask application provides the following API endpoints:

- **GET /api/dashboard/summary**: Returns summary statistics
- **GET /api/children**: Returns information about all children
- **GET /api/alerts**: Returns all active alerts
- **POST /api/alerts/{id}/resolve**: Resolves an alert
- **GET /api/debug**: Returns debug information about the application

## Content Analysis

The system analyzes screen content for:

- Age-appropriateness
- Educational value
- Content category (Games, Education, Social Media, etc.)
- Potential concerns

## Alert Generation

Alerts are generated for:

- Inappropriate content detected
- Excessive screen time
- Potentially harmful activities

## Customization

### Adding New Children

Edit the database directly or modify the `update_alex_data.py` script to include additional children.

### Adjusting Alert Thresholds

Modify the alert generation logic in `update_alex_data.py` to adjust when alerts are triggered.

### Changing the Dashboard Appearance

Modify the CSS in `frontend/css/styles.css` to customize the dashboard's appearance.

## Troubleshooting

### Dashboard Not Loading

- Check that the Flask application is running
- Verify that the frontend files exist in the correct location
- Check the browser console for JavaScript errors

### Data Not Updating

- Ensure the `update_alex_data.py` script is running successfully
- Check database connections and permissions
- Verify that the API endpoints are returning data correctly

### API Errors

- Check the Flask application logs for error messages
- Verify database schema and connections
- Ensure all required tables exist in the database

## Contributors

- **Aniket** (Discord: patelaniket12)
- **Chirag** (Discord: 0_chirag_s)
- **Watermelon** (Discord: melonwaterbottle)
- **ルフィ** (Discord: luffyznft)

## Future Enhancements

- User authentication for multiple parents
- Mobile app integration
- More detailed content analysis
- Weekly and monthly reports
- Customizable screen time limits
- Integration with parental control systems

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Screenpipe API for screen monitoring capabilities
- Google Gemini/Llama for AI content analysis
- Flask for the web framework
- All contributors to the project

---

*This README was last updated on March 3, 2025.*
