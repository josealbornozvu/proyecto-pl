# Aplicación de Programación Lineal: simplex revisado

Proyecto de Optimización (Universidad de Antioquia). Resuelve problemas de programación
lineal con el **simplex revisado** implementado por el equipo y muestra cada iteración.

- **Backend:** Python + FastAPI (`backend/`). El método usa `fractions.Fraction`: sin errores de redondeo.
- **Frontend:** React + Vite (`frontend/`). La gráfica con Plotly.js llega en el Sprint 2.
- **scipy** se usa únicamente en las pruebas, para verificar resultados.

## Requisitos

- Python 3.10 o superior
- Node.js 18 o superior

## Instalación

```bash
# Backend
cd backend
python -m venv .venv
# Windows:     .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements-dev.txt

# Frontend
cd ../frontend
npm install
```

## Ejecución en desarrollo (dos terminales)

```bash
# Terminal 1: backend en http://127.0.0.1:8000
cd backend
uvicorn app.main:app --reload

# Terminal 2: frontend en http://localhost:5173
cd frontend
npm run dev
```

## Ejecución con un solo comando (para la sustentación)

```bash
cd frontend && npm run build        # una sola vez
cd ../backend && uvicorn app.main:app
# Abrir http://127.0.0.1:8000
```

## Pruebas

```bash
cd backend
pytest
```

## Estado por sprint

| Sprint | Alcance |
|---|---|
| 1 | Entrada y validación, simplex revisado con restricciones ≤ (problemas 1, 3, 5, 6, 7 y Wyndor), paso a paso, detección de no acotado, múltiples óptimos y degenerado |
| 2 | Restricciones ≥ y = y lados derechos negativos (dos fases), infactibilidad, método gráfico con Plotly.js, análisis de sensibilidad |
| 3 | Pulido de interfaz, bonificaciones, manual, video y sustentación |
