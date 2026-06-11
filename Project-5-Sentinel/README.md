
# Proyecto 5 — Microsoft Sentinel (SIEM)

## Objetivo
Implementar Microsoft Sentinel como solución SIEM/SOAR para detección
de amenazas, correlación de eventos y respuesta automatizada en Azure.

## Tecnologías utilizadas
- Microsoft Sentinel
- Log Analytics Workspace
- Azure Activity connector
- KQL (Kusto Query Language)
- Analytics Rules

## Pasos realizados

### 1. Creación del Log Analytics Workspace
- Nombre: `law-security-lab`
- Región: East US
- Resource Group: `rg-security-lab`

### 2. Conexión de Microsoft Sentinel
- Sentinel vinculado al workspace `law-security-lab`

### 3. Data Connector — Azure Activity
- Conector instalado y en estado Connected
- Ingesta de logs de actividad de la suscripción

### 4. Analytics Rule — Suspicious Resource Deployment
- Tipo: Scheduled
- Severidad: Low
- Táctica MITRE: Impact (T1496)
- Detecta despliegues inusuales por callers no vistos antes
- Frecuencia: cada 1 día | Período: últimos 14 días

## Capturas

| Archivo | Descripción |
|---------|-------------|
| 01-sentinel-no-workspace.png | Estado inicial sin workspace |
| 02-sentinel-created.png | Sentinel creado |
| 03-sentinel-overview.png | Dashboard overview |
| 04-sentinel-data-connectors.png | Sección Data Connectors |
| 05-sentinel-connectors-connected.png | Conector Azure Activity conectado |
| 06-sentinel-azure-activity-installed.png | Azure Activity instalado |
| 07-analytics-rule-created.png | Regla Analytics en lista |
| 08-analytics-rule-detail.png | Detalle y KQL de la regla |
| 09-law-workspace.png | Log Analytics Workspace activo |

## Habilidades demostradas
- Configuración de SIEM en la nube (Microsoft Sentinel)
- Ingesta de logs con Data Connectors
- Creación de reglas de detección con KQL
- Monitoreo de actividad de recursos Azure

## Relevancia profesional
Microsoft Sentinel es la herramienta SIEM principal en entornos
SOC modernos. Esta configuración demuestra capacidad de detección
de amenazas alineada con roles de SOC Analyst y Security Engineer.