# Facility Intelligence MCP Server

**AI-Powered Energy Infrastructure Intelligence and Safe Action Framework**

An educational Model Context Protocol (MCP) project that enables AI assistants to analyze simulated facility data, identify energy inefficiencies, detect anomalies, assess equipment health, prioritize maintenance, and simulate operational changes safely.

> **Disclaimer:** This is an independent educational prototype. It does not connect to live building-management systems or control physical equipment. All demonstration data is synthetic.

## 1. Project Overview

Facility managers need to monitor energy consumption, HVAC equipment, sensor readings, and maintenance records. Analyzing these datasets manually can make it difficult to identify abnormal conditions and prioritize repairs.

The Facility Intelligence MCP Server exposes reusable tools that allow compatible AI assistants to retrieve structured data, perform facility analysis, and provide recommendations in natural language.

## 2. Objectives

- Analyze energy consumption against baseline values.
- Detect unusual energy usage, vibration, power draw, and equipment runtime.
- Evaluate equipment health and potential failure risks.
- Rank maintenance work orders by priority.
- Estimate the impact and risk of proposed operational changes.
- Provide a standardized interface for AI assistants through MCP.
- Keep operational decisions subject to human review and approval.

## 3. Technology Stack

- Python
- Model Context Protocol (MCP)
- JSON datasets
- Rule-based anomaly detection
- Git and GitHub
- MCP Inspector
- Claude Desktop
- Visual Studio Code with GitHub Copilot

## 4. System Architecture

```text
USER
  |
  v
AI ASSISTANT / HOST
(Claude Desktop / VS Code)
  |
  v
MCP PROTOCOL
  |
  v
FACILITY INTELLIGENCE SERVER
(server.py)
  |
  +-- 6 MCP Tools
  |     |-- get_facility_status
  |     |-- analyze_energy_usage
  |     |-- detect_anomalies
  |     |-- get_equipment_health
  |     |-- prioritize_maintenance
  |     |-- simulate_action
  |
  +-- Resource: facility://summary
  |
  +-- Prompt: facility_analysis
  |
  v
SERVICE LAYER
  |-- facility_service.py
  |-- energy_service.py
  |-- equipment_service.py
  |-- maintenance_service.py
  |-- simulation_service.py
  |
  v
LOCAL JSON DATASETS
  |-- energy.json
  |-- equipment.json
  |-- maintenance.json
  |-- sensors.json
  |
  v
STRUCTURED ANALYSIS RESULTS
  |
  v
AI EXPLANATION AND HUMAN REVIEW
```

## 5. MCP Components

### Tools

| Tool | Description |
|---|---|
| `get_facility_status` | Returns a facility-wide summary. |
| `analyze_energy_usage` | Compares actual and baseline energy consumption. |
| `detect_anomalies` | Identifies unusual conditions using defined rules. |
| `get_equipment_health` | Assesses and ranks equipment risks. |
| `prioritize_maintenance` | Ranks maintenance work orders. |
| `simulate_action` | Estimates the impact and risk of a proposed action without controlling hardware. |

### Resource

`facility://summary` — provides a summary of facility information.

### Prompt

`facility_analysis` — guides the AI assistant through a structured facility-analysis workflow.

## 6. Project Structure

```text
facility-intelligence-mcp/
├── server.py
├── facility_service.py
├── energy_service.py
├── equipment_service.py
├── maintenance_service.py
├── simulation_service.py
├── data/
│   ├── energy.json
│   ├── equipment.json
│   ├── maintenance.json
│   └── sensors.json
├── docs/
│   └── architecture.md
├── README.md
├── pyproject.toml
├── .gitignore
└── .mcp.json
```

## 7. Installation and Setup

### Requirements

- Python 3.10 or later
- Git
- An MCP-compatible host

### Open the project

```powershell
cd B:\facility-intelligence-mcp
```

### Install project dependencies

Use the dependency configuration in `pyproject.toml`. If the project supports editable installation, run:

```powershell
python -m pip install -e .
```

### Validate Python syntax

```powershell
python -m py_compile server.py facility_service.py energy_service.py equipment_service.py maintenance_service.py simulation_service.py
```

## 8. AI Host Integration

### Claude Desktop

1. Open Claude Desktop.
2. Go to Settings → Developer.
3. Confirm that `facility-intelligence` is running.
4. Ask Claude to analyze facility status using the MCP tools.

### Visual Studio Code with GitHub Copilot

1. Open the project folder in VS Code.
2. Verify the MCP configuration.
3. Run `MCP: List Servers` from the Command Palette.
4. Open Copilot Chat in Agent mode.
5. Ask a facility-related question and verify that the tools are used.

## 9. Example User Queries

- Analyze the current facility status.
- Which buildings are consuming more energy than their baselines?
- Identify active equipment anomalies.
- Rank equipment by potential failure risk.
- Which maintenance issues should be addressed first?
- Simulate increasing RTU-3's cooling setpoint by 1°C without performing a real hardware action.

## 10. Sample Demonstration Results

The sample dataset contains:

| Metric | Demonstration result |
|---|---:|
| Buildings | 3 |
| Equipment monitored | 12 |
| Actual daily energy consumption | 11,370.5 kWh |
| Baseline daily consumption | 9,850 kWh |
| Energy above baseline | 1,520.5 kWh |
| Energy variance | +15.44% |
| Open maintenance work orders | 7 |
| Equipment warnings | 6 |

### Energy comparison

| Building | Actual (kWh) | Baseline (kWh) | Variance |
|---|---:|---:|---:|
| Building-A | 3,850.5 | 3,100 | +24.21% |
| Building-B | 2,400 | 2,550 | -5.88% |
| Building-C | 5,120 | 4,200 | +21.90% |

These results are derived from the synthetic demonstration dataset, not live facility measurements.

## 11. Anomaly Detection

The rule-based detection engine checks for conditions such as:

- Energy consumption more than 15% above baseline.
- Vibration above 4.0 mm/s.
- Unusual electrical power draw.
- Excessive equipment operating hours.
- Reported equipment faults.

These are indicators for further investigation, not definitive proof of equipment failure.

## 12. Maintenance Prioritization

Maintenance work orders are scored using safety, reliability, energy impact, and equipment criticality.

The demonstration dataset identifies RTU-3, Cooling-Pump-2, and Chiller-1 among the highest-priority items. Qualified personnel must verify the findings before performing maintenance.

## 13. Safe Action Simulation

The `simulate_action` tool estimates the possible impact of a proposed action and reports its risk, confidence, and safety recommendations.

For example, a demonstration simulation of a 1°C increase in RTU-3's cooling setpoint returned:

- Estimated cooling-load impact: -4.2%.
- Estimated power savings: 1.63 kW.
- Estimated risk: HIGH.
- Confidence score: 82%.
- Hardware modified: `false`.

The tool recommends addressing the active equipment fault before attempting the change. These estimates are illustrative and must not be treated as verified engineering predictions.

## 14. Screenshots and Testing Evidence

The screenshots PDF documents the project's facility analysis, maintenance prioritization, simulation results, and MCP integration testing.

[**View Facility Intelligence MCP Screenshots (PDF)**](./Facility_Intelligence_MCP_Screenshots.pdf)

## 15. Testing

The project has been tested with MCP Inspector and connected AI hosts.

- [x] Facility summary resource
- [x] Facility status tool
- [x] Energy analysis tool
- [x] Anomaly detection tool
- [x] Equipment health tool
- [x] Maintenance prioritization tool
- [x] Safe action simulation tool
- [x] Facility analysis prompt
- [x] Claude Desktop integration
- [x] VS Code MCP integration

## 16. Limitations

- Uses local synthetic JSON data.
- Anomaly detection is rule-based, not a trained machine-learning model.
- Energy-saving values are simulated estimates.
- Does not connect to or control physical equipment.
- Results depend on the completeness and accuracy of the supplied data.

## 17. Future Enhancements

- Authorized real-time sensor integration.
- Historical energy dashboards and trend analysis.
- Predictive maintenance using validated ML models.
- Configurable thresholds and notifications.
- Audit logging and stronger access controls.
- Evaluation using real, appropriately authorized facility datasets.

## 18. Conclusion

The Facility Intelligence MCP Server demonstrates how MCP can expose facility-analysis capabilities to AI assistants through reusable tools, a resource, and a prompt. It combines energy analysis, anomaly detection, equipment risk assessment, maintenance prioritization, and safe simulation to support human decision-making.

## 19. License

A license has not been specified. Add a license file if you intend to distribute the project under an open-source license.
