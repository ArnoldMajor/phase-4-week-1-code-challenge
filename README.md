
# Hero Superpowers API

## Project Overview

This is a **Flask REST API** for tracking superheroes and their superpowers. The API allows users to retrieve heroes, their powers, and create new hero-power relationships.

## Project Setup

### Clone the Repository
```sh
git clone <your-private-repo-url>
cd <your-project-folder>
```

### Create a Virtual Environment
```sh
python -m venv venv
source venv/bin/activate   # On macOS/Linux
venv\Scripts\activate     # On Windows
```

### Install Dependencies
```sh
pip install -r requirements.txt
```

### Set Up the Database
```sh
flask db init
flask db migrate -m "Initial migration"
flask db upgrade
```

### Seed the Database (Optional)
```sh
python seed.py
```

### Run the Server
```sh
python app.py
```
Your API will be available at `http://127.0.0.1:5555`.

## API Endpoints

### Heroes

#### GET /heroes
```json
[
  { "id": 1, "name": "Kamala Khan", "super_name": "Ms. Marvel" },
  { "id": 2, "name": "Doreen Green", "super_name": "Squirrel Girl" }
]
```

#### GET /heroes/:id
```json
{
  "id": 1,
  "name": "Kamala Khan",
  "super_name": "Ms. Marvel",
  "hero_powers": [
    {
      "id": 1,
      "hero_id": 1,
      "power_id": 2,
      "strength": "Strong",
      "power": { "id": 2, "name": "flight", "description": "Allows flight at supersonic speed" }
    }
  ]
}
```

### Powers

#### GET /powers
```json
[
  { "id": 1, "name": "Super Strength", "description": "Grants immense physical strength." },
  { "id": 2, "name": "Flight", "description": "Allows flight at supersonic speed." }
]
```

#### GET /powers/:id
```json
{ "id": 1, "name": "Super Strength", "description": "Grants immense physical strength." }
```

#### PATCH /powers/:id
**Request:**
```json
{ "description": "Updated power description." }
```
**Response:**
```json
{ "id": 1, "name": "Super Strength", "description": "Updated power description." }
```

### Hero Powers

#### POST /hero_powers
**Request:**
```json
{ "hero_id": 3, "power_id": 1, "strength": "Average" }
```
**Response:**
```json
{
  "id": 11,
  "hero_id": 3,
  "power_id": 1,
  "strength": "Average",
  "hero": { "id": 3, "name": "Gwen Stacy", "super_name": "Spider-Gwen" },
  "power": { "id": 1, "name": "Super Strength", "description": "Grants immense physical strength." }
}
```

## Technologies Used

```markdown
- **Flask** (Backend framework)
- **Flask SQLAlchemy** (Database ORM)
- **SQLite** (Database)
- **Postman** (API Testing)
```

