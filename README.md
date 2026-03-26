# Informatik – Herr Neufeld

Unterrichtsmaterial-Website für den Informatikunterricht am Gymnasium.  
Läuft statisch über **GitHub Pages** – alle Inhalte werden in `data.json` verwaltet.

---

## Dateien im Repository

| Datei | Beschreibung |
|---|---|
| `index.html` | Die Website (nicht anfassen nötig) |
| `data.json` | **Hier pflegst du alle Materialien** |

---

## Material hinzufügen

Öffne `data.json` auf GitHub (Stift-Icon → Bearbeiten) und füge einen neuen Eintrag am Anfang des Arrays ein.

### Arbeitsblatt / PDF

```json
{
  "id": 101,
  "type": "pdf",
  "title": "Titel des Arbeitsblatts",
  "topic": "Thema / Kapitel",
  "desc": "Kurze Beschreibung des Inhalts.",
  "klasse": "10a",
  "level": "leicht",
  "url": "https://link-zum-pdf.de/datei.pdf",
  "date": "2025-04-01"
}
```

### Link / Video

```json
{
  "id": 102,
  "type": "link",
  "title": "Name des Links",
  "topic": "Thema / Kapitel",
  "desc": "Kurze Beschreibung.",
  "klasse": "",
  "level": "",
  "url": "https://beispiel.de",
  "date": "2025-04-01"
}
```

### Quiz

```json
{
  "id": 103,
  "type": "quiz",
  "title": "Quiz: Thema",
  "topic": "Thema / Kapitel",
  "desc": "Kurze Beschreibung.",
  "klasse": "11",
  "level": "mittel",
  "url": "",
  "date": "2025-04-01",
  "questions": [
    {
      "q": "Fragetext?",
      "options": ["Option A", "Option B", "Option C", "Option D"],
      "correct": 0
    }
  ]
}
```

> **`correct`** ist der **Index** (0–3) der richtigen Antwort.  
> `"correct": 0` → Option A ist richtig, `"correct": 2` → Option C ist richtig.

---

## Felder im Überblick

| Feld | Pflicht | Mögliche Werte |
|---|---|---|
| `id` | ✅ | Beliebige eindeutige Zahl |
| `type` | ✅ | `"pdf"` · `"link"` · `"quiz"` |
| `title` | ✅ | Beliebiger Text |
| `topic` | – | Beliebiger Text (z. B. `"Python Grundlagen"`) |
| `desc` | – | Beliebiger Text |
| `klasse` | – | z. B. `"10b"`, `"11"`, `""` für keine Angabe |
| `level` | – | `"leicht"` · `"mittel"` · `"schwer"` · `""` |
| `url` | – | Vollständige URL (`https://…`) oder `""` |
| `date` | – | Format `YYYY-MM-DD` |
| `questions` | Nur bei Quiz | Array von Fragen (siehe Beispiel oben) |

---

## Material löschen

Öffne `data.json`, suche den Eintrag nach `"title"` und lösche den gesamten `{ … }`-Block (inkl. dem Komma zum nächsten Eintrag).

---

## GitHub Pages aktivieren

1. Repository → **Settings** → **Pages**
2. Source: **Deploy from a branch** → Branch: `main` / Ordner: `/ (root)`
3. Speichern → Website ist unter `https://DEIN-NAME.github.io/REPO-NAME` erreichbar

---

## PDFs hosten

PDFs können direkt im Repository liegen (z. B. `pdfs/variablen.pdf`).  
Der Link in `data.json` wäre dann: `"url": "pdfs/variablen.pdf"`
