# FastAPI Template

- **A starter kit for FastAPI backend projects** – ready to ship in a Docker container and work out‑of‑the‑box with VS Code Dev‑Containers.

---

## 🚀 Quick Start
```markdown
1️⃣ **Open the repo in VS Code**  
2️⃣ **Press** `Ctrl+Shift+P` → *Dev Containers: Rebuild Container*  
3️⃣ **Wait** for the container to build (Docker Desktop must be running).  
4️⃣ **Forward the API port** to the host:  
   - `Ctrl+,` → Search for `Remote: Local Port Forwarding`.  
   - Add a new entry: `8000 → 8000` (or your FastAPI port).  
   - Choose `All interfaces` if you need external access.  
5️⃣ **Launch the app** inside the container (`uvicorn app.main:app --reload`).  
6️⃣ **Open** `http://localhost:8000/docs` to view the auto‑generated OpenAPI docs.
```
---

## 📦 Prerequisites

- **Docker Desktop** (any recent version)
- **VS Code** with the *Remote - Containers* extension

## 📦 Dependencies
- `uvicorn`, `fastapi`, `pydantic`, etc. – all installed in the container