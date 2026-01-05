# API Automation – Postman + Newman

## Descripción
Framework de automatización de pruebas API orientado a ejecución por CLI e integración CI/CD.

## Estructura
- collections/: Colecciones Postman
- env/: Ambientes
- reports/: Evidencias HTML y JUnit
- docs/: Documentación funcional

## Ejecución
```bash
npx newman run collections/collection.json \
-e env/QA.json \
-r cli,htmlextra,junit
