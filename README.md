# TAPASYA — AI-Powered Urban Heat Risk & Cooling Optimization Engine

TAPASYA is an AI-powered urban cooling decision engine designed to identify areas experiencing high urban heat stress, explain the major factors driving that risk, simulate potential cooling interventions, and prioritize where limited resources should be deployed for maximum expected impact.

## Problem

Urban heat is not distributed equally across a city. Built-up areas, vegetation, surface characteristics, weather conditions, population exposure, and urban morphology can create significant differences in heat stress between nearby locations.

Cities need a practical way to answer:

> WHERE should we intervene, WHAT should we do, and HOW MUCH benefit can we expect?

TAPASYA aims to provide a data-driven decision-support workflow for this problem.

## What TAPASYA Does

TAPASYA follows the pipeline:

**Heat → Human Thermal Stress → Exposure/Risk → WHY → Cooling Scenarios → Resource Optimization → WHERE TO ACT FIRST**

The system:

1. Generates urban heat indicators from satellite and environmental data.
2. Estimates human thermal stress using meteorological conditions.
3. Combines heat exposure with population and urban characteristics.
4. Identifies the major factors associated with thermal risk.
5. Simulates different cooling intervention scenarios.
6. Estimates expected benefits using transparent scenario-based assumptions.
7. Prioritizes intervention locations under limited resources.

## Study Area

The initial pilot study focuses on:

**Gurugram, Haryana, India**

Selected area:

**Municipal Wards 3, 4, 5, 6 and 7**

Approximate contiguous area:

**23.44 km²**

## Data Sources

The project uses geospatial and environmental datasets including:

- **Landsat 8/9 Collection 2 Level-2** — Land Surface Temperature
- **Sentinel-2 Level-2A Surface Reflectance** — NDVI, NDBI and other surface indicators
- **ERA5-Land Hourly** — Temperature, humidity, wind and radiation variables
- **GHSL Population P2023A** — Population exposure
- **GHSL Built-up Surface P2023A** — Built-up characteristics
- **NASA SRTM 30m** — Elevation and derived terrain information
- **OpenStreetMap** — Roads and urban morphology

## AI / ML Approach

The initial machine-learning approach is designed to remain interpretable and practical.

Potential models include:

- Random Forest
- XGBoost

Model interpretation will use feature-attribution techniques such as:

- SHAP

Spatial validation will be used instead of relying only on random pixel-wise train/test splitting, reducing the risk of overly optimistic performance caused by spatial autocorrelation.

Model performance will be evaluated using metrics such as:

- R²
- RMSE
- MAE

## Cooling Intervention Simulator

TAPASYA will compare scenario-based cooling interventions such as:

- Urban greenery
- Cool roofs / increased surface albedo
- Water-based cooling
- Combined interventions

The simulator will use transparent assumptions to estimate potential benefits.

These outputs represent **scenario-based estimates**, not guaranteed physical temperature reductions.

## Resource Optimization

The optimization layer considers factors such as:

- Thermal risk
- Population exposure
- Vulnerability/exposure characteristics
- Intervention suitability
- Expected benefit
- Resource or budget constraints

The objective is to identify locations where available resources can potentially produce the greatest reduction in heat exposure.

## Dashboard

The decision-support interface follows a simple structure:

**WHERE → WHY → WHO → WHAT → HOW MUCH → WHERE FIRST**

This allows urban planners and heat-action authorities to move from identifying a hotspot to understanding its drivers and evaluating possible interventions.

## AWS Architecture

The planned cloud architecture uses AWS services for the deployable decision engine.

```text
Frontend
   ↓
API Gateway
   ↓
AWS Lambda
   ↓
ML / Decision Engine
   ↓
S3 + DynamoDB
   ↓
Results & Dashboard

Amazon Bedrock
   ↓
Natural-language explanation of structured
ML and optimization results
