# rulespec-ec Agent Notes

This repo stores Ecuador RuleSpec source registry materials, oracle references, and encoded policy rules. All encoded law lives under a single `ec/` namespace.

## Scope

- `ec/statutes/`: Ecuadorian laws — the LRTI (Codificación 26) chain, the Ley de Seguridad Social (Ley 55, 2001), the Ley Orgánica para Enfrentar el Conflicto Armado Interno (RO Supl. 516, 2024), and other primary law needed for tax-benefit modeling.
- `ec/regulations/`: executive decrees, reglamentos, and institutional resolutions (IESS C.D. series, SRI NAC resolutions) made under the laws.
- `ec/policies/`: social-protection programme rules set administratively (the MIES Bono de Desarrollo Humano legal-basis record and related programme documents).
- `programs/`: declarative compose specs (one per jurisdiction/program/period).
- `data/coverage/`, `data/oracles/`: coverage backlog and comparison references. These are never legal authority.

## Do

- Start from the furthest upstream source: Registro Oficial texts and official consolidations (SRI compilations, IESS prints, ministry legal-basis records — record the host in manifest metadata), decrees and institutional resolutions next, agency guidance last.
- Add RuleSpec under `ec/statutes/`, `ec/regulations/`, or `ec/policies/` with companion `.test.yaml` files.
- Cite corpus paths from modules via `module.source_verification.corpus_citation_path` (or `corpus_citation_paths`).
- Use the ECUAMOD v5.1 policy window (2011–25) as the validation frame: VAT 12% → 13% (RO 516) → 15% applied from 1 April 2024; PIT Art. 36 tables per year; BDH USD 50 from 2013; SIC category tables per report Tables 2.4–2.10. Indexed/annual values must be corpus-grounded, never invented.
- Keep exact oracle versions in `data/oracles/oracle-index.json`. The SOUTHMOD bundle is licensed and non-redistributable — never commit bundle bytes, dataset rows, or model XML.
- Sync `axiom-encode` and `.axiom/toolchain.toml` before substantial encoding runs.

## Do Not

- Use SRI calculators or third-party tax alerts as the first legal source when a law or instrument governs the rule.
- Invent, round, or interpolate any Ecuadorian monetary amount, rate band, or threshold. Every number must come verbatim from a captured official provision.
- Migrate ECUAMOD, EUROMOD/SOUTHMOD, or agency calculator code mechanically as RuleSpec.
- Add generated source payload dumps, formula artifacts, `parameters.yaml`, or standalone YAML fixtures outside allowed RuleSpec roots.
- Hand-copy statute text into RuleSpec without a corpus `citation_path`.
