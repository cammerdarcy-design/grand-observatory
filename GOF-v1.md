# GEOL Observation Format (GOF) v1.0

## Purpose

The GEOL Observation Format (GOF) defines the canonical structure used by the Grand Observatory of Fantasia to store, exchange, and visualize Grand Eye observations.

Every GEOL observation should be representable using this format.

The Projection Chamber, Observation Library, Atlas, and future visualization tools all consume GOF rather than implementing observation-specific logic.

---

# Core Design Principles

1. Observations are independent of visualization.

2. The Projection Chamber renders observations but never defines them.

3. Every observation has a single focal object.

4. Every observation may contain one or more observational lenses.

5. Nodes represent observed entities.

6. Relations represent observed organizational relationships.

7. Written observations remain part of the canonical record.

---

# Top-Level Structure

```json
{
  "metadata": {},
  "focus": {},
  "lenses": [],
  "constellations": [],
  "observation": {}
}
```

---

# Metadata

```json
{
  "geol": "29",
  "title": "SpaceX Organizational Field Observation",
  "version": "1.0",
  "date": "2026-07-18",
  "status": "Published"
}
```

---

# Focus

Represents the central object of observation.

```json
{
  "name": "SpaceX",
  "type": "Organization"
}
```

---

# Lenses

Each lens represents one observational perspective.

Example:

- Structure
- Flow
- Transformation
- Development
- Evolution

```json
[
  {
    "id":"structure",
    "title":"Organizational Structure",
    "description":"Persistent organizational units."
  }
]
```

---

# Constellations

Each constellation contains nodes and relationships.

```json
{
  "id":"structure",

  "nodes":[
    {
      "id":"engineering",
      "label":"Engineering"
    }
  ],

  "relations":[
    {
      "from":"engineering",
      "to":"manufacturing",
      "type":"supports"
    }
  ]
}
```

---

# Observation Text

The original published GEOL remains part of the file.

```json
{
  "purpose":"...",
  "boundary":"...",
  "questions":[...],
  "text":"..."
}
```

---

# Design Rule

The Projection Chamber SHALL render GOF files without requiring modification for individual observations.

Changing observations should require only new GOF files, never changes to the Projection Chamber.

---

Version 1.0
Grand Observatory of Fantasia
