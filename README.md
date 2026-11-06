# Diftar Ledigingen API

OpenAPI-specificatie voor het opvragen van minicontainer-ledigingen (Diftar) ten
behoeve van de "mijnomgeving" van NL-Portal.

📖 **[Bekijk de API-documentatie](https://jypma-prlg.github.io/diftar-api/)** —
gegenereerd met Redoc, automatisch bijgewerkt bij elke wijziging aan
`diftar-openapi.yaml` (zie [`publiceer-documentatie.yml`](.github/workflows/publiceer-documentatie.yml)).

## Inhoud

- [`diftar-openapi.yaml`](diftar-openapi.yaml) — de API-specificatie (OpenAPI 3.0.3).
- [`GLOSSARY.md`](GLOSSARY.md) — domeinbegrippen.
- [`STANDARDS.md`](STANDARDS.md) — welke standaarden zijn gebruikt en hoe getoetst.
- [`docs/adr/`](docs/adr/) — architectuurbeslissingen (ADR's).

## Doel en herkomst

Dit is een herziening van de eerste, door NewWaste aangeleverde versie van de
API, met als doel een stabiele API die voldoet aan:

- de [NL API-strategie](https://gitdocumentatie.logius.nl/publicatie/api/adr/)
- de [OpenAPI 3.0-standaard](https://spec.openapis.org/oas/latest.html)
- bruikbaarheid voor implementatie in NL-Portal

Zie [`STANDARDS.md`](STANDARDS.md) voor het volledige overzicht van getoetste
standaarden en [`docs/adr/`](docs/adr/) voor de onderbouwing van de belangrijkste
ontwerpbeslissingen (met name de security-aanpak).

## Validatie (CI)

Twee GitHub Actions-workflows valideren elke wijziging aan de spec:

- [`oas3-validatie.yml`](.github/workflows/oas3-validatie.yml) — is het geldig OpenAPI 3.0?
- [`api-design-rules.yml`](.github/workflows/api-design-rules.yml) — voldoet het aan de
  [NL API Design Rules](https://developer.overheid.nl/kennisbank/api-ontwikkeling/standaarden/api-design-rules/)?

Beide workflows roepen dezelfde [mise](https://mise.jdx.dev/)-taken aan die je
ook lokaal draait. Tool- en standaardversies (Redocly CLI, DON Checker,
ADR-versie) staan vastgepind in [`mise.toml`](mise.toml) en worden door
[Renovate](renovate.json) bijgehouden.

Lokaal draaien:

```bash
mise run validate-all
```

Of afzonderlijk:

```bash
mise run validate-oas-spec
```

```bash
mise run validate-nl-api-design-rules
```

## Open punten

- `fractieCode` is nog een vrije string; wordt mogelijk een vastgelegde codelijst
  zodra de leverancier deze aanlevert.
- Servers in de spec zijn placeholders; vullen zodra ontwikkel-/acceptatie-/
  productie-omgevingen bekend zijn.
