# 🤖 Starks Industries — J.A.R.V.I.S Voice Assistant

An intelligent voice assistant developed in Python with speech recognition, home automation, emotion detection via machine learning, and a real-time graphical interface.

---

## 🚀 Features

- 🎙️ Voice command recognition (hotword: **"Pepe"**)
- 🧠 AI-powered conversations via **Groq (LLaMA 3.3-70b)**
- 😊 Emotion detection from voice using a custom trained ML model
- 💡 Home automation via **Arduino + relay** (220V AC control)
- 🎵 Spotify control by voice
- 🌤️ Real-time weather, timers, Google search, web shortcuts
- 🖥️ Graphical interface with animated audio waves
- ⌨️ Text input support alongside voice
- 💾 Persistent conversation history across sessions

---

## 🛠️ Technologies Used

- Python 3.10+
- Groq API (LLaMA 3.3-70b-versatile)
- Scikit-learn (MLPClassifier for emotion detection)
- Librosa (audio feature extraction)
- Edge-TTS (neural text-to-speech)
- SpeechRecognition + Google Speech API
- Spotipy (Spotify Web API)
- Tkinter (graphical interface)
- PySerial (Arduino communication)
- OpenWeatherMap API

---

## 📦 Project Structure

```
├── main.py                  # Main execution file
├── voz.py                   # Voice processing (TTS + STT)
├── comandos.py              # Command handling
├── funciones.py             # Hour, weather, timer, web shortcuts
├── gpt.py                   # Groq AI integration + persistent history
├── emociones.py             # Emotion detection logic
├── domotica.py              # Arduino relay control
├── interfaz.py              # Graphical interface
├── entrenar.py              # ML model training script
├── modelo_emociones.pkl     # Trained emotion model
├── encoder_emociones.pkl    # Label encoder
├── scaler_emociones.pkl     # Feature scaler
├── historial.json           # Persistent conversation history
├── .env.example             # Environment variables template
└── requirements.txt         # Python dependencies
```

---

## ⚙️ Installation

### 1. Clone the repository
```bash
git clone https://github.com/BenjaPalazzo/Virtaul-Asistant-Windows.git
cd Starks-Industries
```

### 2. Create a virtual environment
```bash
python -m venv venv
source venv/bin/activate   # Linux / Mac
venv\Scripts\activate      # Windows
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Configure environment variables

Copy `.env.example` to `.env`:
```bash
cp .env.example .env   # Linux / Mac
copy .env.example .env # Windows
```

Then fill in your own API keys in `.env` (see section below).

### 5. (Optional) Train the emotion detection model

Download the [RAVDESS dataset](https://zenodo.org/record/1188976) — file `Audio_Speech_Actors_01-24.zip` (~215MB), extract it into a `dataset/` folder, then run:

```bash
python entrenar.py
```

### 6. (Optional) Connect Arduino for home automation

Connect your Arduino Uno with a relay module:
- GND → GND
- 5V → VCC  
- Pin 7 → IN

Upload the Arduino sketch (included in `/arduino/domotica.ino`) and update the port in `domotica.py`:
```python
PUERTO = "/dev/ttyACM0"  # Linux
PUERTO = "COM3"           # Windows
```

---

## 🔑 API Keys Setup

All keys go in your `.env` file. Every API listed here has a **free tier**.

| Service | Where to get it | Time |
|---------|----------------|------|
| **Groq** | [console.groq.com](https://console.groq.com) | 2 min |
| **Spotify** | [developer.spotify.com](https://developer.spotify.com/dashboard) | 5 min |
| **OpenWeatherMap** | [openweathermap.org/api](https://openweathermap.org/api) | 2 min |

Your `.env` should look like this:
```
GROQ_API_KEY=your_key_here
SPOTIFY_CLIENT_ID=your_client_id_here
SPOTIFY_CLIENT_SECRET=your_client_secret_here
SPOTIFY_REDIRECT_URI=http://127.0.0.1:8888/callback
SPOTIFY_SCOPE=user-read-playback-state user-modify-playback-state user-read-currently-playing
OPENWEATHER_API_KEY=your_key_here
```

---

## ▶️ Usage

```bash
python main.py
```

Say **"Pepe"** to activate the assistant, then try:

| Command | Action |
|---------|--------|
| "¿Qué hora es?" | Current time and date |
| "¿Cómo está el clima?" | Weather in your city |
| "Poneme un timer de 5 minutos" | Sets a timer |
| "Reproducí Last Night de The Strokes" | Plays on Spotify |
| "Prender luz" | Turns on relay (Arduino) |
| "Apagar luz" | Turns off relay (Arduino) |
| "Charlemos" | Starts AI conversation |
| "¿Cómo me ves?" | Detects your emotion |
| "Abrí YouTube" | Opens YouTube |

You can also type commands directly in the chat interface.

---

## 🧪 Model Training

To retrain the emotion detection model with RAVDESS dataset:

```bash
python entrenar.py
```

Expected accuracy: ~60-65% on CPU without GPU. The model classifies 8 emotions: neutral, calm, happy, sad, angry, fearful, disgust, surprised.

---

## 📌 Roadmap

- [ ] Wake word trained on own voice
- [ ] Flask backend + mobile web frontend
- [ ] Computer vision with YOLO
- [ ] Multi-device home automation
- [ ] Android app

---

## 👨‍💻 Author

Developed by **Benjamín Palazzo**  
Mechatronics Engineering Student — Universidad Nacional de Cuyo  
[GitHub](https://github.com/BenjaPalazzo12)

---

## 📄 License

This project is open-source and available under the MIT License.
