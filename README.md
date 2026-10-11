# Scott Hofmann

Applied AI architect. Fourteen years as a pre-sales solutions architect (OpenText, Micro Focus, Serena) and nineteen years designing and delivering systems in regulated financial services. Since 2023 I build production agentic systems with Claude Code.

Source for the projects below is private. The NW Management projects can be shared with interviewers on request.

## FileValidator (MSUFCU, 2026)

Document/metadata verification for scanned member statements and tax forms. C#/.NET 9 WPF, Python, local LLM. Runs fully on-premises; no member data leaves the machine.

- Pipeline: deterministic Python feature extraction, then an XGBoost classifier, then a local qwen3-coder-30b (LM Studio) reviewer under a strict JSON verdict contract. The reviewer sits behind a deterministic verification gate: the model may dismiss a finding only if its cited evidence is present in the document.
- Result: false positives cut from 283 to 48 (83%) on a 3,931-document batch while surfacing about 40 genuine index/document mismatches; full run unattended in 23 minutes.
- Evaluation: 324 xUnit and 51 Python rule tests, 32 adversarial scenarios against real PDFs, and a capture / synthesize / score harness for comparing candidate prompts on labeled cases.

## Palimpsest (MSUFCU, in production, 2026)

PII discovery and synthetic replacement across folders and databases. Each PII value is replaced with a same-length synthetic one and every location is audited. C#/.NET 9, React, IIS; SQL Server or PostgreSQL.

- Tiered detection: deterministic column rules, then XGBoost, then a local open-weight LLM for ambiguous columns and values. Of 10,482 logged verdicts, 37% were decided by rules, 27% by XGBoost and 36% by the LLM.
- Evaluation harness: every verdict logged with engine, confidence, reason and latency; a 33-test xUnit suite with each run recorded to the database; 13+ local models benchmarked across 317 runs, with Qwen3 selected on performance and size.

## Capital Loom (NW Management, 2026)

Fund-administration platform in daily production use: investor portal, e-signature, double-entry general ledger, deterministic pro forma engine, QuickBooks integration and generated signable offering packages. Blazor Server / .NET 10 on Azure. Built in about two months with Claude Code and Claude Design.

- AI-assisted deal intake: a Claude Code skill fills a model-agnostic JSON profile contract from listing brochures and POSTs batches through tool use, with no manual data entry.
- 600+ tests, including FsCheck property tests, a 30+-invariant reconciliation validator on every calculation, statement tie-outs that gate document generation and baseline-diff regression of generated packages; hardened by two Claude-run adversarial code reviews (138 findings).

## Parcelytix (NW Management, 2026)

AI-assisted civil site development: zoning compliance, preliminary design, permits. .NET 10 / React / PostGIS, built from a Claude Design specification.

- Provider-agnostic AI routing on the Anthropic SDK with an OpenAI-compatible adapter (Claude, GLM, open models).
- Agentic civil-engineering tasks, for example maximizing the number of lots in a subdivision under the governing ordinances. Reads real Civil 3D drawings (DWG/DXF via ACadSharp) in about a second, with no AutoCAD required.

## Design principle

Measure the model, don't trust it. Model judgments sit behind deterministic verification, and every rule traces back to a real case and the measurement that justified it.

## Elsewhere

- Talks: "Guerrilla AI," SpartaHack 11 (Jan 2026); Solidity and smart contracts, Apple Developer Academy Detroit (Apr 2026); "Coding with AI," MSUFCU Engineering (Jul 2026)
- Co-author, *IIS 6: The Complete Reference* (McGraw-Hill Osborne, 2003)
- [linkedin.com/in/scotthofmann](https://www.linkedin.com/in/scotthofmann) · scott@scottrhofmann.com
