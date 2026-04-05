<p align="center">
  <strong>
    <span style="color: #000000;">R</span><span style="color: #75BFAF;">A</span><span style="color: #75BFAF;">I</span><span style="color: #000000;">L</span>
  </strong>
</p>

<h3 align="center">Responsible AI Labs</h3>

<p align="center">
  Evaluate, monitor, and improve the safety and fairness of AI systems.<br/>
  API-first. 8 dimensions. Production-ready.
</p>

<p align="center">
  <a href="https://pypi.org/project/rail-score-sdk/">
    <img src="https://img.shields.io/pypi/v/rail-score-sdk?style=flat-square&label=PyPI&color=75BFAF" alt="PyPI Version" />
  </a>
  <a href="https://pypi.org/project/rail-score-sdk/">
    <img src="https://img.shields.io/pypi/dm/rail-score-sdk?style=flat-square&label=PyPI%20Downloads&color=2D6B5A" alt="PyPI Downloads" />
  </a>
  <a href="https://www.npmjs.com/package/@responsible-ai-labs/rail-score">
    <img src="https://img.shields.io/npm/v/@responsible-ai-labs/rail-score?style=flat-square&label=npm&color=75BFAF" alt="npm Version" />
  </a>
  <a href="https://www.npmjs.com/package/@responsible-ai-labs/rail-score">
    <img src="https://img.shields.io/npm/dm/@responsible-ai-labs/rail-score?style=flat-square&label=npm%20Downloads&color=2D6B5A" alt="npm Downloads" />
  </a>
  <a href="https://www.drupal.org/project/rail_score">
    <img src="https://img.shields.io/badge/Drupal-rail__score-0678BE?style=flat-square&logo=drupal&logoColor=white" alt="Drupal" />
  </a>
  <a href="https://arxiv.org/abs/2505.00204">
    <img src="https://img.shields.io/badge/arXiv-2505.00204-b31b1b?style=flat-square&logo=arxiv&logoColor=white" alt="arXiv" />
  </a>
  <a href="https://huggingface.co/responsible-ai-labs">
    <img src="https://img.shields.io/badge/HuggingFace-Datasets-FFD21E?style=flat-square&logo=huggingface&logoColor=000" alt="HuggingFace" />
  </a>
  <a href="https://github.com/Responsible-AI-Labs/rail-score-sdk/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-22C55E?style=flat-square" alt="License" />
  </a>
</p>

<p align="center">
  <a href="https://responsibleailabs.ai">Website</a> &middot;
  <a href="https://docs.responsibleailabs.ai">Docs</a> &middot;
  <a href="https://pypi.org/project/rail-score-sdk/">PyPI</a> &middot;
  <a href="https://www.npmjs.com/package/@responsible-ai-labs/rail-score">npm</a> &middot;
  <a href="https://huggingface.co/responsible-ai-labs">HuggingFace</a> &middot;
  <a href="https://arxiv.org/abs/2505.00204">Paper</a>
</p>

---

## What is RAIL?

RAIL Score is an API-first platform that evaluates AI-generated content across **8 independent dimensions** on a 0-10 scale:

> **Fairness** · **Safety** · **Reliability** · **Transparency** · **Privacy** · **Accountability** · **Inclusivity** · **User Impact**

Each evaluation returns per-dimension scores, confidence levels, issue detection, and actionable improvement suggestions. Not a single opaque number, but a full diagnostic.

### Core capabilities

**Evaluation** -- Score any AI output with basic (~1 credit) or deep (~3 credits) analysis, with custom dimension weights for healthcare, finance, legal, and general contexts.

**Safe Regeneration** -- Evaluate-improve-regenerate loop that runs until your thresholds are met. Server-side or client-side with your own LLM.

**Compliance Testing** -- 63 requirements across 6 frameworks: GDPR, HIPAA, EU AI Act, CCPA, India DPDP Act, India AI Governance. Single API call.

**Agent Evaluation** -- Tool call evaluation (ALLOW/FLAG/BLOCK), tool result scanning with PII redaction, and prompt injection detection across 5 attack patterns.

**Policy Engine & Middleware** -- `RAILMiddleware` wraps any generate function. `PolicyEngine` enforces per-dimension thresholds. `RAILSession` tracks multi-turn risk.

---

## Packages

| Package | Registry | Install |
|---|---|---|
| **Python SDK** | [![PyPI](https://img.shields.io/pypi/v/rail-score-sdk?style=flat-square&color=75BFAF)](https://pypi.org/project/rail-score-sdk/) [![Downloads](https://img.shields.io/pypi/dm/rail-score-sdk?style=flat-square&color=2D6B5A)](https://pypi.org/project/rail-score-sdk/) | `pip install rail-score-sdk` |
| **JavaScript/TypeScript SDK** | [![npm](https://img.shields.io/npm/v/@responsible-ai-labs/rail-score?style=flat-square&color=75BFAF)](https://www.npmjs.com/package/@responsible-ai-labs/rail-score) [![Downloads](https://img.shields.io/npm/dm/@responsible-ai-labs/rail-score?style=flat-square&color=2D6B5A)](https://www.npmjs.com/package/@responsible-ai-labs/rail-score) | `npm install @responsible-ai-labs/rail-score` |
| **Drupal Module** | [![Drupal](https://img.shields.io/badge/drupal.org-rail__score-0678BE?style=flat-square&logo=drupal&logoColor=white)](https://www.drupal.org/project/rail_score) | `composer require drupal/rail_score` |

### Provider extras (Python)

```
pip install rail-score-sdk[openai]       # GPT-4o, GPT-4o-mini
pip install rail-score-sdk[anthropic]    # Claude 3.5, Claude 3
pip install rail-score-sdk[google]       # Gemini 1.5 Pro/Flash
pip install rail-score-sdk[litellm]      # LiteLLM guardrail support
pip install rail-score-sdk[integrations] # All providers
```

---

## Quick start

### Python

```python
from rail_score_sdk import RAILClient

client = RAILClient(api_key="your-api-key")

result = client.evaluate(
    content="Your AI-generated text here",
    mode="deep",
    domain="healthcare"
)

for dim in result.dimensions:
    print(f"{dim.name}: {dim.score}/10 (confidence: {dim.confidence})")
```

### JavaScript / TypeScript

```typescript
import { RAILClient } from '@responsible-ai-labs/rail-score';

const client = new RAILClient({ apiKey: 'your-api-key' });

const result = await client.evaluate({
  content: 'Your AI-generated text here',
  mode: 'deep',
  domain: 'healthcare'
});

result.dimensions.forEach(dim => {
  console.log(`${dim.name}: ${dim.score}/10`);
});
```

### LLM wrappers (drop-in replacements)

```python
from rail_score_sdk.wrappers import RAILOpenAI

client = RAILOpenAI(api_key="your-api-key", openai_api_key="sk-...")
# Every response is automatically scored
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Summarize this report"}]
)
print(response.rail_score)  # Full 8-dimension evaluation attached
```

---

## Datasets & Research

| Resource | Description |
|---|---|
| [RAIL-HH-10K](https://huggingface.co/datasets/responsible-ai-labs/RAIL-HH-10K) | 10,000 examples with 73 columns of 8-dimension scoring, built on Anthropic's HH dataset |
| [Indian Responsible AI Benchmark](https://huggingface.co/datasets/responsible-ai-labs/indian-responsible-ai-benchmark) | 212 adversarial prompts across 22 India-specific categories (caste bias, regional sensitivity, linguistic nuance) |
| [arXiv 2505.00204](https://arxiv.org/abs/2505.00204) | "RAIL in the Wild: Operationalizing Responsible AI Evaluation Using Anthropic's Value Dataset" |

---

## Integrations

RAIL plugs into your existing stack:

| Integration | What it does |
|---|---|
| **Langfuse** | Trace-level RAIL scores in your observability pipeline |
| **LiteLLM** | `RAILGuardrail` for the LiteLLM proxy |
| **OpenTelemetry** | Export to Datadog, Grafana, Jaeger, or any OTEL backend |
| **OpenAI / Anthropic / Gemini** | Drop-in LLM wrappers that score every response |
| **React / Next.js / Vue.js** | JS SDK works across frontend frameworks |

---

## Compliance coverage

RAIL tests 63 requirements across 6 regulatory frameworks in a single API call:

| Framework | Requirements | Status |
|---|---|---|
| GDPR | 12 | Supported |
| HIPAA | 11 | Supported |
| EU AI Act | 14 | Supported |
| CCPA | 8 | Supported |
| India DPDP Act | 9 | Supported |
| India AI Governance | 9 | Supported |

RAIL is the only evaluation platform where India DPDP Act and India AI Governance are native, first-class compliance frameworks.

---

## Repositories

| Repo | Description |
|---|---|
| [rail-score-sdk](https://github.com/Responsible-AI-Labs/rail-score-sdk) | Python SDK (sync/async, middleware, batch, sessions, agent eval) |
| [rail-score-js](https://github.com/Responsible-AI-Labs/rail-score-js) | JavaScript/TypeScript SDK (wrappers, middleware, policy engine, sessions) |
| [rail-score-drupal](https://github.com/Responsible-AI-Labs/rail-score-drupal) | Drupal CMS integration module |

---

## Links

| | |
|---|---|
| Website | [responsibleailabs.ai](https://responsibleailabs.ai) |
| Documentation | [docs.responsibleailabs.ai](https://docs.responsibleailabs.ai) |
| PyPI | [pypi.org/project/rail-score-sdk](https://pypi.org/project/rail-score-sdk/) |
| npm | [npmjs.com/package/@responsible-ai-labs/rail-score](https://www.npmjs.com/package/@responsible-ai-labs/rail-score) |
| HuggingFace | [huggingface.co/responsible-ai-labs](https://huggingface.co/responsible-ai-labs) |
| arXiv | [arxiv.org/abs/2505.00204](https://arxiv.org/abs/2505.00204) |
| X | [@RAILabsIndia](https://x.com/RAILabsIndia) |
| LinkedIn | [company/rail-ai](https://www.linkedin.com/company/rail-ai/) |

---

<p align="center">
  <sub>
    <strong>
      <span>R</span><span style="color: #75BFAF;">A</span><span style="color: #75BFAF;">I</span><span>L</span>
    </strong>
    &nbsp;&middot;&nbsp; Responsible AI Labs Pvt. Ltd. &nbsp;&middot;&nbsp; Built in India, built for everywhere.
  </sub>
</p>
