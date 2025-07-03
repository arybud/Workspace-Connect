# WorkspaceConnect

A **location-aware coworking space discovery platform** built with **Flask**, **Google Maps API**, and **PostgreSQL**. It helps users quickly **find, compare, and filter** coworking spaces across Delhi NCR (or any region you choose to configure). Real-time distance calculations, pricing filters, and a modern UI make it easy to discover the perfect workspace.

---

## Table of Contents
- [Short Description](#short-description)
- [Features](#features)
- [Screenshots](#screenshots)
- [Installation](#installation)
  - [Prerequisites](#prerequisites)
  - [Setup Steps](#setup-steps)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Short Description
A **Flask-based coworking space discovery tool** leveraging **Google Maps** and **PostgreSQL** for real-time distance, pricing, and feature comparisons across 30+ locations. Includes geolocation, interactive maps, and easy CSV-to-DB loading for instant data updates.

---

## Features
1. **Real-Time Distance Calculation**  
   Utilizes Google Maps and HTML Geolocation to measure user-to-space distance on the fly.

2. **Dynamic Filters & Search**  
   Quickly filter by opening/closing times, price, and food availability. Real-time search for coworking space names.

3. **Interactive Map & Directions**  
   Displays directions from the user’s location to the coworking space, leveraging the Google Maps Directions Service.

4. **Data-Driven**  
   Backed by a PostgreSQL database, automatically populated with CSV data—no manual entries needed.

5. **Responsive UI**  
   Fully functional on mobile devices. Sub-second search results ensure a seamless user experience.

---

## Screenshots

### 1. Homepage
![Homepage](./images/homepage_screenshot.png)

### 2. Filter View
![Filter](./images/filter_screenshot.png)

### 3. Search View
![Search](./images/search_screenshot.png)

### 4. Coworking Space Details
![Space Details](./images/details_screenshot.png)

---

## Installation

### Prerequisites
1. **Python 3+**
2. **PostgreSQL** (running locally or on a server)
3. **Google Maps API key** (enable the **Maps JavaScript API**, **Places API**, and **Geocoding API** in your [Google Cloud Console](https://console.cloud.google.com/))
4. **Git** for cloning/forking the repository

### Setup Steps

1. **Clone or Fork the Repository**
    ```bash
    git clone https://github.com/arybud/workspace-connect.git
    cd workspace-connect
    ```
2. **Create a Virtual Environment** (recommended)
    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On Windows use: venv\Scripts\activate
    ```
3. **Install Dependencies**
    ```bash
    pip install -r requirements.txt
    ```
4. **Configure Environment Variables**
    - Copy `.env.example` to `.env`:
      ```bash
      cp .env.example .env
      ```
    - Edit `.env` and set your Google Maps API key:
      ```
      GOOGLE_MAPS_API_KEY=your_google_maps_api_key
      ```
    - *(Optional)* add `DATABASE_URI` if you want to override the default
      `postgresql://postgres:postgres@localhost:5432/coworking_db`.
      The application loads variables from `.env` automatically.
5. **Create the Database (in PostgreSQL)**
    ```bash
    CREATE DATABASE coworking_db;
    ```
    Or update the config in app.py if you prefer a different database name

6. **Load Sample Data**
    ```bash
    python data_load.py
   ```

7. **Run the Application**
    ```bash
    python app.py
    ```
By default the application will start at http://127.0.0.1:5000
    
## Usage

1. **Visit the Homepage**  
   - Go to [http://127.0.0.1:5000/](http://127.0.0.1:5000/) in your browser.  
   - Allow location access when prompted for geolocation functionality.

2. **Search & Filter**  
   - Use the search bar to find spaces by name (requires at least 3 characters).  
   - Filter by opening time, closing time, and maximum price.

3. **View Space Details**  
   - Click any listed coworking space to see:  
     - Opening/closing times  
     - Price  
     - Food availability  
     - Interactive map and route from your location  

4. **Add or Modify Data**  
   - Update the CSV (or create your own) and rerun `data_load.py` to refresh the database.


## Project Structure

```bash
workspace-connect/
├── app.py                  # Main Flask application
├── data_load.py            # CSV to DB ingestion script
├── coworking_spaces.csv    # Sample data for coworking spaces
├── templates/
│   ├── index.html          # Homepage with search & filters
│   └── coworking_space.html# Detailed coworking space view
├── static/
│   ├── css/
│   │   └── style.css       # Stylesheet
│   └── js/
│       └── script.js       # Front-end JavaScript
└── requirements.txt        # Python dependencies
```

## Contributing
1. Fork the repo on GitHub.
2. Create a feature branch: git checkout -b feature/my-new-feature.
3. Commit your changes: git commit -am 'Add a new feature'.
4. Push to the branch: git push origin feature/my-new-feature.
5. Open a Pull Request in this repository.


## License

This project is distributed under the [MIT License](LICENSE).

---

## Contact

For feedback, issues, or collaboration requests, please open an [issue](https://github.com/arybud/workspace-connect/issues) or reach out via email at **aryanbudhiraja108@gmail.com**.
