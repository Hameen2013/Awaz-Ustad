# 🎙️ Awaz Ustad: Speak, Learn & Connect in Pashto, Hindko & English

**Awaz Ustad** ("Voice Teacher") is an AI voice-based learning game for children aged 8–14. A child says a word in **Pashto, Hindko or English**, and the AI recognises it and teaches the same word in the other two languages, with a picture and a recorded pronunciation.

🔗 **Live demo:** https://hameen2013.github.io/Awaz-Ustad/

---

## 🏆 Competition

| | |
|---|---|
| **Event** | KPITB AI Innovation Challenge 2026 (Khyber Pakhtunkhwa Information Technology Board) |
| **Category** | AI Rising Stars (Interactive) |
| **Theme** | Culture: 01 Local Languages |
| **Status** | Shortlisted for on-site presentation (Reference ID: AIC26-CB2C1529) |

## 👦 Team Awaz Ustad

| Name | Class | Role |
|---|---|---|
| **Muhammad Hameen Faraz** | 8R | Chose and checked the words, recorded voice samples, trained and tested the model, recorded pronunciations, presents the Learn demo |
| **Malik Hamdan Elahi** | 5P | Tested the Game, opens the presentation, presents the Game demo |

**School:** Peshawar Model School, Boys 3, Peshawar
**Teacher mentor:** Sir Basit Khan (English Teacher)

---

## 💡 The problem

Many children in Khyber Pakhtunkhwa find English hard, and our own languages need care to stay alive. Pashto is spoken across most of KP, with many accents. Hindko is spoken only in some areas, and many young Hindko speakers now speak Urdu instead.

Awaz Ustad makes learning languages fun, using our own voices.

## ✨ Features

- **📖 Learn mode:** say a word in any of the three languages. The app shows a picture, highlights the language you spoke, and plays the word in the other two languages.
- **⭐ Game mode:** a picture appears, and the child says its name in any language. A correct answer earns a star, and 5 stars earns the **Zabaan Hero** 🏆 badge.
- **🗂️ All Words:** tap any word to hear it in Pashto, Hindko and English.
- **🧠 How AI Hears:** live confidence bars show how sure the AI is about each word it hears.

## 📚 The words

| | English | Pashto | Hindko |
|---|---|---|---|
| 🐈 | Cat | Pisho · پیشو | Billi · بلی |
| 💧 | Water | Oba · اوبه | Paani · پانی |
| 🌙 | Moon | Spogmay · سپوږمۍ | Chann · چن |
| 🌸 | Flower | Gul · ګل | Phull · پھل |
| 👁️ | Eye | Starga · سترګه | Akh · اکھ |

The Pashto and Hindko words were checked with family members.

---

## 🎧 Dataset

| Item | Details |
|---|---|
| Words | 5 words × 3 languages = **15 word classes** |
| Word samples | 30 per class, **450** in total |
| Background noise | **225** samples (room sounds, fan, quiet talking) |
| Total samples | **675** |
| Format | 1-second audio clips, recorded in Teachable Machine |
| Recorded by | Muhammad Hameen Faraz and family members |

The raw dataset is stored separately in the team's Google Drive (`KPITB Innovation Challenge 2026/Dataset`).

## 🤖 Model

| Item | Details |
|---|---|
| Tool | Google Teachable Machine (Audio Project) |
| Model type | TensorFlow.js Speech Commands (`BROWSER_FFT`): sound is turned into a spectrogram, and a neural network learns each word's pattern |
| Classes | 16: `Background Noise` plus 15 word classes, named `<word>_<language>` (e.g. `cat_ps`, `cat_hk`, `cat_en`) |
| Training | 50 epochs |
| Results | ≈100% training accuracy; **≈93% test accuracy** (on samples the model did not train on) |
| Online model | https://teachablemachine.withgoogle.com/models/B7aIszlfE/ |
| Offline copy | `my_model/` folder in this repository (used by the app) |

The app accepts a word only when the model is at least **80%** sure. You can change this with `THRESHOLD` in `index.html`.

## 🔊 Pronunciation clips (`audio/`)

| Files | Source |
|---|---|
| `*_ps.mp3` (Pashto), `*_hk.mp3` (Hindko) | Recorded by the team |
| `*_en.mp3` (English) | Computer-generated voice (Piper text-to-speech) |

---

## 📁 Repository structure

```
Awaz-Ustad/
├── index.html            The app (Learn, Game, All Words, How AI Hears)
├── my_model/             Trained Teachable Machine model
│   ├── model.json
│   ├── metadata.json
│   └── weights.bin
├── lib/                  TensorFlow.js libraries (so the app also works offline)
│   ├── tf.min.js
│   └── speech-commands.min.js
├── audio/                Pronunciation clips: <word>_<ps|hk|en>.mp3
├── START-Windows.bat     Runs the app offline on a Windows laptop
└── README.md
```

## ▶️ How to run

**Online:** open https://hameen2013.github.io/Awaz-Ustad/ → press **Start** → allow the microphone → say a word.

**Offline (no internet):**
1. Download this repository (**Code → Download ZIP**) and unzip it.
2. Double-click **`START-Windows.bat`**. Python must be installed. Or, in a terminal inside the folder, run:
   ```
   python -m http.server 8000
   ```
   and open http://localhost:8000.
3. Press **Start** and allow the microphone.

⚠️ Don't open `index.html` by double-clicking it. The browser blocks the model and the microphone that way. Use the online link or `localhost`.

**Tips:** use a headset or clip-on microphone in noisy places, and speak each word clearly, once.

---

## 🤝 How we used AI

- **Teachable Machine** trained the voice-recognition model from our own recordings.
- **Claude** helped write and debug the web-page code and generated the English pronunciation clips.
- The idea, word selection, voice data, Pashto and Hindko recordings, game design and testing were done by the team.

## 🚀 Future vision

With KPITB's local-language voice and text data, Awaz Ustad could grow:
- **From 5 words to thousands**, with topic packs (animals, food, body, home) and more voices and accents.
- **More languages:** Khowar, Torwali, Kohistani and Saraiki.
- **Words to sentences:** speech-to-text trained on local-language data, so children can speak full sentences.
- **Works offline** on low-cost phones in rural schools.

> *"Today Awaz Ustad knows 15 words. With KPITB's language data, it can help every child in KP learn English and every language of our province."*

---

**Team Awaz Ustad** · Peshawar Model School, Boys 3, Peshawar · KPITB AI Innovation Challenge 2026
Thank you · Manana · Shukria
