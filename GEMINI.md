# COSTITUZIONE DEL PROGETTO — SoftwareHouse_Trenin

Leggi sempre `docs/spec.md` e `docs/plan.md` prima di creare o modificare qualsiasi file.

## 1. Stack Tecnologico (Da finalizzare Sabato 09:30)
- **Frontend (`/frontend`):** Next.js (App Router), TypeScript strict, Tailwind CSS
- **Backend API & Auth (`/backend/api`, `/backend/auth`, `/backend/db`):** Python 3.11+, FastAPI, Pydantic v2
- **Core Engine (`/backend/engine`):** Python puro deterministico / AI logic (zero dipendenze HTTP/DB dirette)
- **Database & Auth:** PostgreSQL su Supabase (`auxxuhnbmjuuinmrixgi`)

## 2. Regole di Sicurezza & Multi-Tenancy (NON NEGOZIABILI)
- **Zero segreti nel codice:** API key, JWT secret, connection string e password vanno SOLO in `.env` / `.env.local`.
- **Multi-tenancy obbligatoria:** ogni tabella di dominio deve avere il tenant key (`tenant_id` / `gym_id`), e ogni query/endpoint protetto deve filtrare rigorosamente per il tenant dell'utente autenticato.
- **Validazione esplicita:** tutte le richieste e risposte API devono essere validate con schemi Pydantic / TypeScript (Zod).

## 3. Regole dei 3 Recinti & Workflow
- Lavora **solo su branch dedicati** (`feat/...`), mai direttamente su `main`.
- Modifica esclusivamente i file dentro il tuo recinto assegnato (`backend/api|auth|db`, `backend/engine`, oppure `frontend`).
- Ogni nuova funzione in `/backend` deve includere test `pytest` (happy-path + edge-case).
- Verifica sempre che test e build passino prima di proporre il diff o aprire una Pull Request.
