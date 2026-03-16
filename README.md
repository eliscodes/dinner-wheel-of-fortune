# 🍽️ DinnerSpin

> **Was kochen wir heute Abend?** — Das Glücksrad für Abendessen-Ideen, Nährwert-Tracking und automatische Einkaufslisten für Spar & Hofer.

![Static Badge](https://img.shields.io/badge/Sprache-Deutsch-green)
![Static Badge](https://img.shields.io/badge/Tech-Vanilla%20HTML%2FCSS%2FJS-orange)
![Static Badge](https://img.shields.io/badge/API-Spoonacular-blue)
![Static Badge](https://img.shields.io/badge/Deployment-GitHub%20Pages-black)

---

## 🎯 Was ist das?

DinnerSpin löst die ewige Frage: **„Was kaufe ich diese Woche ein – und was kochen wir eigentlich?"**

Ein Fortune-Wheel das zufällig ein Abendessen vorschlägt, mit vollständigem Rezept, Nährwertangaben je nach Person und einer automatisch generierten Einkaufsliste sortiert nach Spar und Hofer.

---

## ✨ Features

| Feature | Beschreibung |
|---|---|
| 🎰 **Glücksrad** | Zufälliges Abendessen per Spin – das Rezept unter dem Zeiger wird nach dem Stoppen ausgelesen |
| 👫 **Personen-Modus** | Nährwerte für *Beide*, *Nur er* oder *Nur sie* – Portionsgrößen passen sich automatisch an |
| ⚗️ **Multi-Filter** | Mehrere Filter gleichzeitig kombinierbar: Wenig Kalorien + Viel Protein + Unter 30 Min. |
| 📊 **Nährwerte** | kcal, Protein, Ballaststoffe, Kohlenhydrate, Fett – pro Rezept und Portion |
| 📖 **Vollrezept** | Zutaten, Schritt-für-Schritt Anleitung und Koch-Tipp direkt in der App |
| 📅 **Wochenplan** | 7 Tage automatisch befüllen, einzelne Tage neu mischen |
| 🛒 **Einkaufsliste** | Automatisch nach 🟢 Spar und 🟠 Hofer sortiert, abhakbar, exportierbar |
| 🌐 **Spoonacular API** | Täglich neue Rezepte aus der API, auf Deutsch übersetzt |
| 🔌 **API-Quota-Anzeige** | Live-Anzeige der verbleibenden API-Punkte im Header mit Warnung bei niedrigem Stand |

---

## 🥘 Eigene Rezepte (immer verfügbar)

12 handverlesene Rezepte als feste Basis – auch wenn die API nicht erreichbar ist.

---

## 🚀 Deployment auf GitHub Pages

### Option 1 – Direkt hochladen (empfohlen)

1. Neues Repo auf [github.com/new](https://github.com/new) erstellen
2. `index.html` und `README.md` hochladen via **Add file → Upload files**
3. **Settings → Pages → Source: Deploy from a branch → main / root**
4. App ist live unter `https://YOURNAME.github.io/dinner-wheel-of-fortune/`

### Option 2 – Per Git

```bash
git clone https://github.com/YOURNAME/dinner-wheel-of-fortune.git
cd dinner-wheel-of-fortune
# index.html und README.md reinkopieren
git add .
git commit -m "🍽️ DinnerSpin initial"
git push origin main
```


---

## 🔌 APIs

### Spoonacular (Rezepte + Nährwerte)
- **Plan:** Free — 50 Punkte/Tag
- **Verbrauch:** ~2 Punkte für einen Batch von 12 Rezepten, 1 Punkt pro Vollrezept-Abruf
- **Caching:** Batch-Ergebnisse werden 24h in `localStorage` gecacht → typisch 2–3 Punkte/Tag
- **Fallback:** Bei leerem Quota oder Netzwerkfehler laufen die 12 eigenen Rezepte weiter
- Backlink required: [spoonacular.com](https://spoonacular.com)

### MyMemory (Übersetzung EN → DE)
- **Plan:** Kostenlos, kein API-Key nötig
- **Einsatz:** Übersetzt Rezeptname, Küche, Zutaten und Zubereitungsschritte der API-Rezepte
- **Caching:** Alle übersetzten Texte werden dauerhaft in `localStorage` gecacht

---

## 🛠️ Eigene Rezepte hinzufügen

In `index.html` das Array `EIGENE_REZEPTE` erweitern:

```js
{
  id: 10013,              // eindeutige ID (10000er-Bereich für eigene)
  name: 'Mein Gericht',
  emoji: '🥙',
  küche: 'Libanesisch · Schnellküche',
  tags: ['schnell', 'viel-protein'],  // siehe gültige Tags unten
  vegetarisch: false,
  zeit: 25,               // Minuten
  quelle: 'https://...',  // optional, null wenn keins
  quelleText: 'Rezept-Quelle',
  vonApi: false,
  er:  { kcal: 580, protein: 40, ballaststoffe: 5, fett: 18, kh: 52 },
  sie: { kcal: 440, protein: 31, ballaststoffe: 4, fett: 13, kh: 40 },
  zutaten: [
    { name: 'Hähnchenschenkel 600 g', laden: 'hofer' },
    { name: 'Zitrone 2 Stk.', laden: 'spar' },
    // laden: 'spar' oder 'hofer'
  ],
  schritte: [
    'Schritt 1...',
    'Schritt 2...',
  ],
  tipp: 'Optionaler Koch-Tipp.',
},
```

**Gültige Tags:** `viel-protein` · `wenig-kcal` · `viel-ballaststoffe` · `schnell` · `vegetarisch`

---

## 📐 Nährwert-Ziele (Kalorien-Balken)

| Modus | Ziel Abendessen |
|---|---|
| 👫 Beide | ~700 kcal (Ø) |
| ♂ Nur er | ~800 kcal |
| ♀ Nur sie | ~600 kcal |

Basierend auf ca. 2000–2500 kcal Tagesbedarf, Abendessen ≈ 35%.

---

## 🗺️ Roadmap

- [ ] Mehr eigene Rezepte (Ziel: 20+)
- [ ] Saisonale Vorschläge (Sommer / Winter)
- [ ] Wochenplan als PDF exportieren
- [ ] Budget-Tracker pro Einkauf
- [ ] Serverless Proxy für API-Key (Netlify / Vercel)

---

## 📄 Lizenz

MIT — frei verwendbar, guten Appetit. 🍳

---

*Rezept-Daten von [Spoonacular](https://spoonacular.com) · Übersetzung von [MyMemory](https://mymemory.translated.net)*
