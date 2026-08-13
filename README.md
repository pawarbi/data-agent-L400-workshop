# Fabric Data Agent L400 Workshop

> **DRAFT workshop material:** These resources are under active development and may change before the workshop is delivered.

This repository contains the data, semantic models, notebooks, evaluation assets, and lab instructions for the Microsoft Fabric Data Agent L400 workshop.

## Deploy the workshop assets

Download [`NB_Deploy_Workshop_Assets.ipynb`](NB_Deploy_Workshop_Assets.ipynb) and execute this notebook in Fabric. The workspace must be attached to a Fabric capacity.

By default, the notebook deploys the workshop notebooks and semantic models to the workspace where it is executed. You can optionally provide another workspace ID. Set `TARGET_FOLDER_ID` to deploy into an existing root or nested folder; otherwise, the notebook creates or reuses the root folder named `data_agent_lab`.

When semantic-model refresh is enabled, the deployment notebook creates or reuses a shareable Anonymous Web connection for the public GitHub datasource, binds it, and refreshes both models. Connection setup and refresh are disabled by default. No GitHub credential or token is required.

The evaluation, judge-calibration, and OpsRef Lakehouse notebooks expose `DATA_SOURCE_REF`. It defaults to `main`; use an immutable release tag or commit for reproducible workshop runs.

## Prerequisites
  •	A paid F2 or higher Fabric capacity, or a Power BI Premium per capacity (P1 or higher) capacity with Microsoft Fabric enabled.

  •	Enable cross-geo processing and cross-geo storing for AI based on requirements explained in Fabric data agent tenant settings.

  •	Power BI Pro license

  •	At least a Contributor role in a workspace

  •	Familiarity with Power BI, DAX, Python, SQL

## Repository contents

| Folder | Contents |
| --- | --- |
| [`data`](data/) | Manufacturing operations source data used by the workshop |
| [`eval`](eval/) | Evaluation sets and judge-calibration assets |
| [`lab-instructions`](lab-instructions/) | Participant lab guide in PDF format |
| [`semantic-models`](semantic-models/) | Baseline and AI-ready Power BI semantic models |
| [`notebooks`](notebooks/) | Fabric setup, evaluation, calibration, and Lakehouse notebooks |

## Workshop assets

### Lab instructions

- [Fabric Data Agent Workshop Labs - Aug 2026](lab-instructions/Fabric%20Data%20Agent%20Workshop%20Labs%20-%20Aug%202026.pdf)

### Semantic models

- [Manufacturing Ops](semantic-models/Manufacturing%20Ops.pbix)
- [Manufacturing Ops AI Ready](semantic-models/Manufacturing%20Ops%20AI%20Ready.pbix)

### Notebooks

- [`NB_Deploy_Workshop_Assets.ipynb`](NB_Deploy_Workshop_Assets.ipynb) - Root deployment notebook for the complete workshop environment.
- `NB_DataAgent_SDK_Setup_L400.ipynb`
- `NB_DataAgentEval_L400.ipynb`
- `NB_JudgeCalibration_L400.ipynb`
- `NB_OpsRefLakehouse_Build_and_Views_L400.ipynb`
