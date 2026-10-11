# Graficador 3D F(x,y,z,t)=0

App de escritorio con pywebview (Python + HTML/JS) para graficar superficies implícitas 3D,
empaquetable como instalador para Windows y con sistema de actualización vía GitHub Releases.

## Estructura del proyecto

```
PRIMERA APP PC/
├── backend/          # Código Python: ventana pywebview, API puente JS<->Python,
│                      # cálculo de la superficie (marching cubes), lógica de versión/update
├── frontend/          # HTML/CSS/JS: UI y visualización 3D (Three.js)
├── build_scripts/     # Scripts para compilar con PyInstaller y generar el instalador
├── installer/         # Script de Inno Setup (.iss) y el instalador final (.exe)
├── requirements.txt   # Dependencias Python
└── README.md
```

## Entorno verificado en PC1 (2026-10-11)

- Python 3.13.3
- Git 2.56.0
- Node v24.15.0 / npm 12.0.2
- SO destino (PC2): Windows 8.1, 2GB RAM → se evita Electron, se usa pywebview (liviano).
  pywebview en Windows usa el motor WebView2 de Microsoft Edge, compatible con Windows 8.1,
  pero PC2 probablemente no lo tenga preinstalado: el instalador final deberá incluir el
  "WebView2 Runtime Bootstrapper" para instalarlo automáticamente si falta.

## Plan de fases

0. Preparar entorno y estructura (ESTE PASO)
1. App funcional en modo desarrollo (backend + frontend + ventana pywebview)
2. Empaquetar backend+frontend como ejecutable standalone (PyInstaller)
3. Convertir en instalador real (Inno Setup) -> generar v1.0.0, instalar en PC2
4. Sistema de actualización (GitHub Releases + botón "Actualizar")
5. Generar v1.1/v2 en PC1, subir, actualizar PC2 y validar el ciclo completo
6. (Futuro) Mejoras: React, más funciones, firma digital del instalador, etc.
