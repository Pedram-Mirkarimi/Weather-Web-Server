<div align="center">

# 🌤️ WeatherNow — Weather Forecast Web App

A dynamic **weather web app** built with **Node.js**, **Express**, and **Handlebars (hbs)**.  
**Learning project** focused on consuming external APIs: **Mapbox Geocoding** (address → coordinates) and **OpenWeatherMap** (live weather).  
Emphasis on clean routing, input validation, and user-friendly error messages.

<br/>

![Node.js](https://img.shields.io/badge/Node.js-Backend-339933?logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-Web%20Server-000000?logo=express&logoColor=white)
![Handlebars](https://img.shields.io/badge/Handlebars-hbs-orange)
![Mapbox](https://img.shields.io/badge/Mapbox-Geocoding-1A1A1A?logo=mapbox&logoColor=white)
![OpenWeather](https://img.shields.io/badge/OpenWeatherMap-Weather-FF7A00)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-F7DF1E?logo=javascript&logoColor=000)

</div>

---

## 📌 Table of Contents
- [✨ Features](#-features)
- [🧰 Tech Stack](#-tech-stack)
- [🧩 How It Works](#-how-it-works)
- [📁 Project Structure](#-project-structure)
- [🚀 Getting Started](#-getting-started)
- [🔑 Environment Variables](#-environment-variables)
- [📡 Endpoints](#-endpoints)
- [👤 Author](#-author)

---

## ✨ Features
- 🧭 Address → coordinates via **Mapbox**
- 🌦️ Weather data via **OpenWeatherMap**
- 🧩 Pages rendered with **hbs** templates (layouts/partials)
- 🧼 Simple frontend with client-side fetch to `/weather`
- 🧯 Helpful error messages for invalid requests

---

## 🧰 Tech Stack

| Category | Technology |
|---|---|
| Backend | Node.js, Express |
| Templates | hbs (Handlebars) |
| HTTP Client | request |
| Geocoding | Mapbox API |
| Weather | OpenWeatherMap API |
| Frontend | HTML/CSS/JS (static in `public/`) |
> **Note:** This project currently uses `request` (legacy). A migration to `fetch`/`axios` is planned.

---

## 🧩 How It Works
1. User enters an address in the UI.
2. Browser calls: `GET /weather?address=...`
3. Server calls Mapbox to get `{ latitude, longitude, location }`
4. Server calls OpenWeatherMap with coordinates
5. Server returns `{ forecast, location, address }` to the browser

---

## 📁 Project Structure

```txt
weathernow-web/
├─ src/
│  ├─ app.js
│  └─ utils/
│     ├─ geocode.js
│     └─ forecast.js
├─ public/
│  ├─ css/
│  └─ js/
│     └─ app.js
├─ templates/
│  ├─ partials/
│  └─ views/
│     ├─ index.hbs
│     ├─ about.hbs
│     ├─ help.hbs
│     └─ 404.hbs
└─ package.json
````

---

## 🚀 Getting Started

### ✅ Prerequisites

* Node.js installed

### 📥 Install

```bash
npm install
```

### 🔑 Create `.env`

Create a `.env` file in the project root (same level as `package.json`):

```env
PORT=3000
MAPBOX_TOKEN=your_mapbox_token
OPENWEATHER_KEY=your_openweather_key
```

> Important:
>
> * Do NOT commit `.env` to git.
> * Make sure `app.js` loads env vars using:
>   `require('dotenv').config();`

### ▶️ Run

```bash
npm start
```

Server default:

* `http://localhost:3000`

---

## 🔑 Environment Variables

| Variable          | Required | Description                             |
| ----------------- | -------: | --------------------------------------- |
| `PORT`            |       No | Server port (default: 3000)             |
| `MAPBOX_TOKEN`    |      Yes | Mapbox access token for geocoding       |
| `OPENWEATHER_KEY` |      Yes | OpenWeatherMap API key for weather data |

---

## 📡 Endpoints

| Method | Route                  | Description           |
| -----: | ---------------------- | --------------------- |
|    GET | `/`                    | Weather page          |
|    GET | `/about`               | About page            |
|    GET | `/help`                | Help page             |
|    GET | `/weather?address=...` | Returns JSON forecast |
|    GET | `/help/*`              | Help 404              |
|    GET | `*`                    | Global 404            |

**Example:**

```bash
curl "http://localhost:3000/weather?address=Berlin"
```

---

## Error handling
- Handles missing/invalid address input
- Shows user-friendly messages for API/network errors

---

## 👤 Author

**S. AmirMohammad Mirkarimi**
GitHub: [S-AmirMohammad-Mirkarimi](https://github.com/S-AmirMohammad-Mirkarimi)
