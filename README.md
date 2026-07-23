# Hp-DAC

Code developed under the project *Hp-DAC: Desenvolvimento de Estratégias
Avançadas para Otimização do Desempenho de Bombas de Calor em Sistemas de
Captura Direta de CO₂*, executed by POLO – Laboratórios de Pesquisa em
Refrigeração e Termofísica (EMC/UFSC) under the ANP R&D investment clauses
(Resolução ANP nº 918/2023), with Repsol Sinopec Brasil.

The repository holds the thermodynamic and thermoeconomic models of the heat
pump and of its coupling to the DAC 15TA reactor, together with the shared
utilities used to produce figures and tables for reports and papers.

## Scope

- **Heat pump models** — vapour compression cycles, high-temperature
  configurations, component sub-models, steady-state and transient operation.
- **DAC thermal system** — thermal demand of the DAC 15TA reactor, heat and
  energy loss accounting, waste heat recovery.
- **Grid models** — renewable generation (solar, wind) and grid supply,
  thermal and electrical energy storage, and dispatch of the coupled
  generation–storage–heat pump system.
- **Thermoeconomics** — CAPEX/OPEX models and Levelized Cost of Carbon
  Capture (LCCC) calculations.
- **Shared utilities** — standard matplotlib style and plotting functions,
  LaTeX table writers, unit handling and property-library wrappers.
