# Earthquake Prediction Application

This project is an earthquake prediction application that utilizes machine learning to forecast potential earthquake occurrences based on historical data. The application is built using Flask for the web framework and includes a user-friendly interface for visualizing predictions.

## Project Structure

```
earthquake-prediction-app
├── src
│   ├── harsha.py                # Main application logic for the earthquake prediction app
│   ├── templates
│   │   └── index.html           # HTML template for displaying predictions and user interactions
│   ├── static
│   │   ├── css                  # Directory for CSS files
│   │   ├── js                   # Directory for JavaScript files
│   │   └── assets               # Directory for static assets (images, fonts, etc.)
│   └── utils
│       └── helpers.py           # Helper functions for code reusability
├── requirements.txt             # Python dependencies for the project
├── README.md                    # Documentation for the project
└── .gitignore                   # Files and directories to be ignored by Git
```

## Setup Instructions

1. **Clone the Repository**
   ```
   git clone <repository-url>
   cd earthquake-prediction-app
   ```

2. **Create a Virtual Environment**
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install Dependencies**
   ```
   pip install -r requirements.txt
   ```

4. **Run the Application**
   ```
   python src/main.py
   ```
   The application will be accessible at `http://127.0.0.1:5002`.

## Usage

- Open your web browser and navigate to the application URL.
- Use the slider to select a future date for earthquake predictions.
- The map will display predicted earthquake locations based on the selected date.

## Contributing

Contributions are welcome! Please submit a pull request or open an issue for any enhancements or bug fixes.

## License

This project is licensed under the MIT License. See the LICENSE file for details.