# rulespec-ec

Ecuador RuleSpec source registry.

This repository targets the Ecuadorian tax-benefit surface simulated by ECUAMOD (the SOUTHMOD tax-benefit microsimulation model for Ecuador, UNU-WIDER; v5.1, policy years 2011–25): personal income tax under the Ley de Régimen Tributario Interno (Codificación 26; Art. 36 annually indexed schedule), VAT under LRTI Art. 65 (twelve percent through March 2024; thirteen percent per the Ley Orgánica para Enfrentar el Conflicto Armado Interno, RO Suplemento 516 de 12-mar-2024; fifteen percent applied from 1 April 2024 under that law's presidential enablement), ICE excises (LRTI Título Tercero), IESS social insurance contributions under the Ley de Seguridad Social (Ley 55, 2001; operative percentage splits in IESS board resolutions), and the Bono de Desarrollo Humano (Executive Decree chain to DE 1395/2013, USD 50 per month).

All encoded law lives under a single `ec/` namespace. The validation frame is ECUAMOD v5.1 (report CR-ECUAMOD-v5.1, Tables 2.4–2.14 for the applied year-by-year values).

## Source Priority

Policy must come from the furthest upstream available source: Registro Oficial texts and official consolidations first (the SRI's LRTI compilations and normative library, the IESS's published Ley de Seguridad Social print, ministry legal-basis records — record the host in manifest metadata), executive decrees and institutional resolutions next, agency guidance only after the governing instrument is identified.

## Listing gates

This repo carries `app_visibility = "experimental"` in `.axiom/registry.toml` and stays out of app surfaces until:

1. The encoded surface covers the flagship calculation (personal income tax gross-to-net for a formal employee) end to end with companion tests.
2. Oracle parity suites exist and pass against ECUAMOD for the encoded surface.
3. Citation paths are stable (ley/Codificación-number form against the Registro Oficial prints).
