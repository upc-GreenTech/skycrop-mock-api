# SkyCrop Mock API

Mock API para las vistas de SkyCrop, basada en learning-center-platform-mock-main del profesor. Conserva MockApiServerConfig, MockApiServer y server.js con json-server 0.17.4.

## Ejecutar

Requiere Node.js 24 o superior.

```bash
npm ci
npm start
```

Dirección local: http://localhost:3000/api/v1. PORT cambia el puerto y JSON_SERVER_DB_PATH permite indicar otro archivo de datos existente. Los registros se guardan en db.json.

## Recursos

- `users`
- `userProfiles`
- `accounts`
- `subscriptionPlans`
- `subscriptions`
- `payments`
- `recoveryCodes`
- `twoFactorAuthentications`
- `plots`
- `plotUsers`
- `plotInvitations`
- `crops`
- `drones`
- `droneConfigurations`
- `flightRoutes`
- `flights`
- `aerialImages`
- `monitoringSessions`
- `diagnoses`
- `anomalies`
- `terrainMaps`
- `reports`
- `reportDiagnoses`
- `notifications`
- `plotMaps`
- `terrainData`
- `agronomicRules`
- `diagnosticHistories`
- `contactMessages`

Se basan en las historias, diagramas de clases y modelo de datos del reporte. Los nombres usan camelCase; agricultural_plots se expone como plots para coincidir con el frontend.

## Usar desde las vistas

Cada colección permite GET y POST; cada registro permite GET, PUT, PATCH y DELETE.

```text
GET    /api/v1/plots
POST   /api/v1/plots
GET    /api/v1/plots/1
PATCH  /api/v1/plots/1
DELETE /api/v1/plots/1
GET    /api/v1/crops?plotId=1
GET    /api/v1/notifications?userId=1
```

Ejemplo de parcela:

```json
{
  "name": "Parcela Norte",
  "areaHectares": 2.5,
  "location": "Lima",
  "createdAt": "2026-10-09T10:00:00Z",
  "status": "ACTIVE"
}
```

Los registros incluyen id; las referencias usan campos como userId, plotId, droneId, routeId, diagnosisId y reportId. JSON Server asigna el identificador al crear un registro. Las asociaciones plotUsers y reportDiagnoses también necesitan id para modificarlas individualmente.

GET / enumera los recursos. GET /api/v1/health comprueba el estado del servidor.

La base empieza vacía. Es CRUD para desarrollar vistas: no valida relaciones ni ejecuta autenticación, pagos, correos, vuelos o análisis de imágenes. Esos procesos requieren implementación adicional. No guardar datos reales de credenciales o tarjetas.

El despliegue en Azure se configura por separado para este nuevo repositorio.
