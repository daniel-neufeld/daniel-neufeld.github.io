# Informatik – Herr Neufeld

Unterrichtsmaterial-Website · Gymnasium · GitHub Pages  
Alle Inhalte werden in `data.json` verwaltet.

---

## Struktur

Die Website ist dreistufig aufgebaut:

```
Jahrgangsstufe  →  Thema  →  Material
```

Das spiegelt sich direkt in `data.json` wider:

```json
[
  {
    "stufe": "10",
    "label": "Jahrgangsstufe 10",
    "themen": [
      {
        "id": "python-grundlagen",
        "titel": "Python Grundlagen",
        "beschreibung": "Kurze Beschreibung des Themas.",
        "material": [
          { ... },
          { ... }
        ]
      }
    ]
  }
]
```

---

## Neue Jahrgangsstufe hinzufügen

Füge am Ende des äußeren Arrays `[ ]` einen neuen Block ein:

```json
{
  "stufe": "9",
  "label": "Jahrgangsstufe 9",
  "themen": []
}
```

> `stufe` muss **eindeutig** sein (wird intern als ID verwendet).

---

## Neues Thema hinzufügen

Füge im `"themen"`-Array der gewünschten Stufe einen neuen Block ein:

```json
{
  "id": "netzwerke",
  "titel": "Netzwerke & Internet",
  "beschreibung": "Wie das Internet funktioniert – Protokolle, IP-Adressen, HTTP.",
  "material": []
}
```

> `id` muss **innerhalb der Stufe eindeutig** sein (nur Kleinbuchstaben, Bindestriche).

---

## Material hinzufügen

Füge im `"material"`-Array des gewünschten Themas einen neuen Eintrag ein.

### Arbeitsblatt / PDF

```json
{
  "id": 401,
  "type": "pdf",
  "title": "Titel des Arbeitsblatts",
  "desc": "Kurze Beschreibung.",
  "level": "mittel",
  "url": "pdfs/dateiname.pdf",
  "date": "2025-05-01"
}
```

### Link / Video

```json
{
  "id": 402,
  "type": "link",
  "title": "Name des Links",
  "desc": "Kurze Beschreibung.",
  "level": "",
  "url": "https://beispiel.de",
  "date": "2025-05-01"
}
```

### Quiz

```json
{
  "id": 403,
  "type": "quiz",
  "title": "Quiz: Thema",
  "desc": "Kurze Beschreibung.",
  "level": "leicht",
  "url": "",
  "date": "2025-05-01",
  "questions": [
    {
      "q": "Fragetext?",
      "options": ["Option A", "Option B", "Option C", "Option D"],
      "correct": 0
    }
  ]
}
```

> **`correct`** ist der **Index** der richtigen Antwort (0 = A, 1 = B, 2 = C, 3 = D).

---

## Felder im Überblick

| Feld | Pflicht | Werte |
|---|---|---|
| `id` | ✅ | Eindeutige Zahl (global über alle Einträge) |
| `type` | ✅ | `"pdf"` · `"link"` · `"quiz"` |
| `title` | ✅ | Beliebiger Text |
| `desc` | – | Beliebiger Text |
| `level` | – | `"leicht"` · `"mittel"` · `"schwer"` · `""` |
| `url` | – | Vollständige URL oder relativer Pfad, `""` für keinen Link |
| `date` | – | Format `YYYY-MM-DD` |
| `questions` | Nur bei Quiz | Array von Fragen (siehe oben) |

---

## Eintrag löschen

Öffne `data.json`, suche den Eintrag anhand von `"title"` oder `"id"` und lösche den gesamten `{ … }`-Block (inkl. dem Komma zum nächsten Eintrag).

---

## PDFs hosten

PDFs direkt im Repository ablegen (z. B. im Ordner `pdfs/`):

```
mein-repo/
├── index.html
├── data.json
└── pdfs/
    ├── variablen.pdf
    └── schleifen.pdf
```

In `data.json` dann mit relativem Pfad verlinken:

```json
"url": "pdfs/variablen.pdf"
```

---

## GitHub Pages aktivieren

1. Repository → **Settings** → **Pages**
2. Source: **Deploy from a branch** → Branch: `main` / Ordner: `/ (root)`
3. Speichern → Seite erscheint unter `https://DEIN-NAME.github.io/REPO-NAME`
