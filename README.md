# AI-Powered PC Hardware Recommendation & E-Commerce System

Full MVP includes:
- Next.js frontend pages (`/`, `/products`, `/compare`, `/build`, `/ai-advisor`, `/auth`)
- ASP.NET Core backend APIs (auth, products, compatibility, price analysis, AI bridge, build suggest, value scores)
- Python FastAPI AI rules engine
- MSSQL schema script with seed data

## Project Structure

```text
AI_PC_Hardware_Project/
  frontend/
  backend/
  ai-service/
  database/
  docs/
```

## Start The Project

## 1) Start Database (Option A: local SQL Server)
- Create database `PCRecommenderDB`.
- Run `database/schema.sql` in SQL Server Management Studio.

## 1) Start Database (Option B: Docker SQL Server)
From project root:

```bash
docker compose up -d sqlserver
```

Then run `database/schema.sql` against `localhost,1433`.

## 2) Start AI Service
Open terminal in `ai-service`:

```bash
pip install -r requirements.txt
uvicorn main:app --reload --port 8010
```

Health check:

```bash
http://localhost:8010/health
```

## 3) Start Backend
Open terminal in `backend`:

```bash
dotnet restore
dotnet run
```

Swagger:

```bash
http://localhost:5000/swagger
```

## 4) Start Frontend
Open terminal in `frontend`:

```bash
npm install
npm run dev
```

Frontend:

```bash
http://localhost:3000
```

## Endpoints Implemented
- `POST /api/auth/register`
- `POST /api/auth/login`
- `GET /api/products`
- `GET /api/products/{id}`
- `POST /api/compatibility/check`
- `GET /api/price/analysis/{productId}?budget=1000`
- `POST /api/ai/recommend`
- `POST /api/build/suggest`
- `GET /api/valuescores`

## Notes
- Backend currently uses in-memory sample product data for fast demo startup.
- SQL schema is included and ready for full database integration.
- AI service rules are fully active in `ai-service/main.py`.
- PSU tiers can be maintained with `database/psu_tiers.csv`.

