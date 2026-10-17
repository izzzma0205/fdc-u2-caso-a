# Actividad Integradora — Unidad 2 · Fundamentos de Ciencia de Datos

**TecNM · Ingeniería en Sistemas Computacionales**
**Caso A:** Arquitectura de Software (Monolito vs. Microservicios)

Pregunta de ingeniería: *¿la sobrecarga de red en microservicios incrementa la latencia respecto a un monolito?*

## Integrantes
- Moreno Rogel Erick - 22090700
- Avilez Delgado Ismael - 22090589
- Bautista Díaz Martín Antonio - 22090601

## Estructura del repositorio
```
.
├── data/
│   ├── dataset_caso_a.csv          # dataset original (500 registros, 250 por grupo)
│   └── dataset_caso_a_limpio.csv   # dataset depurado (criterio 1.5×IQR)
├── notebooks/
│   └── actividad_integradora_u2_caso_a.ipynb   # cuaderno ejecutable y documentado
├── docs/
│   ├── reporte_tecnico.pdf         # reporte final
│   ├── resultados.json             # cifras reportadas (generadas por el cuaderno)
│   └── figuras/                    # gráficas generadas por el cuaderno
├── requirements.txt
└── README.md
```

## Cómo reproducir los resultados
```bash
git clone <URL-DEL-REPOSITORIO>
cd <carpeta-del-repositorio>
python -m venv .venv
source .venv/bin/activate        # En Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/actividad_integradora_u2_caso_a.ipynb
```
Ejecutar el cuaderno de principio a fin (*Run All*). El dataset se genera con semilla fija (42), por lo que los resultados son reproducibles.

## Resumen de resultados
| Concepto | Resultado |
|---|---|
| Observaciones tras depuración | 483 (240 Monolito · 243 Microservicios) |
| Media de latencia | Monolito 123.20 ms · Microservicios 124.61 ms |
| IC 95 % para μ (global) | (119.81, 128.02) ms |
| IC 95 % para μ₁ − μ₂ | (−6.80, 9.63) ms → **0 ∈ IC** |
| Prueba t unilateral (α = 0.05) | t = 0.338 · p = 0.368 → **No rechazar H₀** |

**Conclusión:** no hay evidencia estadística de que microservicios incremente la latencia media; se recomienda ampliar la muestra antes de comprometer SLAs estrictos (la potencia de la prueba es limitada para efectos pequeños).
