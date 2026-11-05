
# Aplicación de Programación Lineal: simplex revisado


Proyecto Curso Optimización 

Universidad de Antioquia

Resuelve problemas de programación lineal con el **simplex revisado**


**Integrantes**
- Sebastian Molina
- Jose Fernando Albornoz

## Estructura del proyecto

- **Backend:** Python + FastAPI (`backend/`). El método usa `fractions.Fraction`: sin errores de redondeo.
- **Frontend:** React + Vite (`frontend/`). La gráfica con Plotly.js llega en el Sprint 2.
- **scipy** se usa únicamente en las pruebas, para verificar resultados.

## Requisitos

- Python 3.10 o superior
- Node.js 18 o superior

## Instalación

```sh
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

## Método elegido
El equipo implementará el simplex revisado, escrito por nosotros desde cero. No se implementará Gran M.
En cada iteración el método trabaja con la matriz base B y su inversa:

- Valores de las variables básicas: X_B = B⁻¹ b
- Valor de la función objetivo: Z = C_B B⁻¹ b
- Prueba de optimalidad: z_j − c_j = C_B B⁻¹ P_j − c_j para las variables no básicas
- Variable que entra: la de z_j − c_j más negativo
- Columna de trabajo: α = B⁻¹ P_j
- Variable que sale: la de menor razón X_B / α entre los α > 0

**Problemas generales**. Los problemas de minimización se convierten a maximización. Las restricciones ≥ y = se resuelven con variables de exceso y artificiales mediante el simplex revisado de dos fases, y los lados derechos negativos se normalizan multiplicando la restricción por −1.

**Casos especiales**. La aplicación informará con un mensaje claro cuando el problema sea infactible (una artificial queda en la base con valor positivo), no acotado (todos los elementos de α son ≤ 0), con soluciones óptimas múltiples (una variable no básica con z_j − c_j = 0) o degenerado (una variable básica vale 0 o hay empate en la razón mínima).
Sensibilidad. Se calcula a partir del tablero final: precios sombra (C_B B⁻¹), costos reducidos, rango de cada coeficiente de la función objetivo y rango de cada lado derecho.

## Ejecución en desarrollo (dos terminales)

```sh
# Terminal 1: backend en http://127.0.0.1:8000
cd backend
uvicorn app.main:app --reload

# Terminal 2: frontend en http://localhost:5173
cd frontend
npm run dev
```

## Ejecución con un solo comando (para la sustentación)

```sh
cd frontend && npm run build        # una sola vez
cd ../backend && uvicorn app.main:app
# Abrir http://127.0.0.1:8000
```

## Pruebas

```sh
cd backend
pytest
```
