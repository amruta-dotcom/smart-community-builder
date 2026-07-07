# Smart Community Builder

A web app that helps people **find nearby community support** — hospitals, clinics, food banks, shelters, and hotels/hostels — using live, real-world location data. It also includes a small AI assistant that understands what kind of help someone needs just from a sentence they type.

🔗 **Live Demo:** _add link here once GitHub Pages is enabled_

![Community Builder preview](./images/hero_illustration_1773080503146.png)

---

## 📖 Overview

Smart Community Builder lets a user enter their location (or use their current GPS location), pick a category, and instantly see nearby support services pulled from **live OpenStreetMap data** — not a hardcoded list. Each result shows distance, address, hours, and status, and can be bookmarked to a personal dashboard.

An **AI Help Assistant** chat widget lets users type a plain-English description of their problem (e.g. *"I need a place to sleep tonight"*) and a small machine learning model classifies it into the right support category and runs the search automatically.

## ✨ Features

- 📍 **Location-based search** — enter an address or use "Locate Me" (browser Geolocation API)
- 🗺️ **Live nearby results** via OpenStreetMap's Overpass API — no fake/hardcoded data
- 🏷️ **Category filtering** — Food Banks, Healthcare, Shelters, Hotels/Hostels
- 🤖 **AI Help Assistant chatbot** — describes your problem in plain language, and a trained Naive Bayes model routes you to the right service category
- 🔖 **Bookmark/save centers** to a personal dashboard view
- 🙋 **Volunteer sign-up** and **donation** modals
- 🔔 Toast notifications for user actions
- 📱 Fully responsive, single-page app–style view switching (no page reloads)

## 🛠️ Tech Stack

**Frontend**
- HTML5
- [Tailwind CSS](https://tailwindcss.com/) (via CDN)
- Vanilla JavaScript
- [Feather Icons](https://feathericons.com/)
- Google Fonts (Inter, Port Lligat Sans)

**APIs & Data**
- Browser Geolocation API — detect user's current location
- [Nominatim](https://nominatim.org/) (OpenStreetMap) — geocoding location names into coordinates
- [Overpass API](https://overpass-api.de/) — live queries for nearby hospitals, clinics, shelters, food banks, and lodging

**AI Backend**
- [Flask](https://flask.palletsprojects.com/) + [Flask-CORS](https://flask-cors.readthedocs.io/) — lightweight local API server
- [scikit-learn](https://scikit-learn.org/) — `CountVectorizer` + `MultinomialNB` for simple intent classification (food / shelter / clinic / hotel)

## 📂 Project Structure

```
smart-community-builder/
├── index.html          # Main app (rename from index2.html — see note below)
├── ai_server.py         # Flask + scikit-learn backend for the AI Help Assistant
├── images/
│   ├── hero_illustration_1773080503146.png
│   └── nearby_support_1773080610353.png
├── requirements.txt      # Python dependencies (see below)
└── README.md
```

> ⚠️ **Note:** The current file is named `index2.html`. Rename it to `index.html` so it works as the default entry point (required for GitHub Pages), and make sure image paths still point to `images/...` after the rename.

## 🚀 Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/amruta-dotcom/smart-community-builder.git
cd smart-community-builder
```

### 2. Run the frontend
Just open `index.html` in your browser — no build step needed.

### 3. (Optional) Run the AI Help Assistant backend
The chatbot widget calls a local Flask server at `http://127.0.0.1:5050/predict`. To enable it:

```bash
pip install -r requirements.txt
python ai_server.py
```

The server will start on port `5050`. Keep it running alongside the open `index.html` page for the AI assistant to respond.

### `requirements.txt`
```
flask
flask-cors
scikit-learn
```

## 🧠 How the AI Assistant Works

The user types a free-text message (e.g. *"I am hungry"* or *"need a place to sleep"*). A `CountVectorizer` turns it into a feature vector, and a `MultinomialNB` classifier — trained on a small labeled dataset of example phrases — predicts one of four categories: `food_bank`, `shelter`, `clinic`, or `hotel`. The frontend then auto-selects that category and runs the live search.

## 🗺️ Roadmap / Future Improvements

- [ ] Expand the AI training data for more accurate intent detection
- [ ] Deploy the Flask backend (e.g. Render/Railway) so the AI assistant works on the live demo, not just localhost
- [ ] Replace the pseudo-distance calculation with accurate Haversine distance
- [ ] Persist bookmarks/dashboard data (currently resets on refresh)
- [ ] Add automated tests

## 🤝 Contributing

Contributions, issues, and feature requests are welcome — feel free to check the [issues page](https://github.com/amruta-dotcom/smart-community-builder/issues).

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](./LICENSE) file for details.

## 👤 Author

**Amruta**
- GitHub: [@amruta-dotcom](https://github.com/amruta-dotcom)

---

⭐️ If you found this project interesting, consider giving it a star!
