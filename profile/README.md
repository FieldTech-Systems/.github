# FieldTech Systems

FieldTech builds software for industrial field service. The FieldTech Platform takes in what customers send a service company (portal requests, email, texts, data-plate photos), works out what they need and how urgent it is, and puts it in front of the right person. Around it sit the facility and equipment records those companies maintain, a manufacturer document library the platform answers from, and the plant-floor telemetry coming off customer sites. Preston Refrigeration is the first service provider on it.

Every repository here is private to the organization.

## Repositories

| Repo | What it is | Stack |
|---|---|---|
| [**flur**](https://github.com/FieldTech-Systems/flur) | The FieldTech Platform: API, customer portal (web and mobile), Admin staff app, document worker. AI triage and routing of inbound messages, the equipment model, the document center and grounded equipment Q&A. | .NET 10, Blazor, MAUI, PostgreSQL + pgvector, Dapper, FluentMigrator, .NET Aspire, AWS CDK |
| [**sparkplug-decode**](https://github.com/FieldTech-Systems/sparkplug-decode) | Sparkplug B data lake prototype. Ignition publishes over MQTT to AWS IoT Core, raw messages land in S3 as Bronze, and a Lambda decodes them into Silver Parquet for Athena. Holds the decoder, CLI tools, the Lambda and the CloudFormation templates. | Python 3.12, protobuf, AWS IoT Core, S3, Lambda, Athena |
| [**claude-mods**](https://github.com/FieldTech-Systems/claude-mods) | Our Claude Code plugin marketplace: `github-activity`, `turn-timestamps` and `connecteam-timeclock`. | TypeScript |
| [**zoho-creator**](https://github.com/FieldTech-Systems/zoho-creator) | Widgets for our Zoho Creator apps. | HTML, JavaScript |

## Names

**Flur** is the platform's code name and stays inside the code (`Flur.slnx`, `Flur.Api`, the `flur` schema). Customers, staff and anyone outside engineering see **FieldTech** or **the FieldTech Platform**.

## How we work

Decisions that shape the system get a numbered ADR in the repo's `docs/adr/`, and multi-step work gets a plan in `docs/plans/` before it starts. Each repo keeps a `CLAUDE.md` at its root; Claude Code is the main way code gets written here, so keep that file current when conventions change.

Anything that reaches a customer or writes to an outside system ships behind its own switch (`Off`, `DryRun`, `Live`) and starts at `Off`. Flur records what it would send rather than sending it, and each real outbound path is listed in the 00-system-overview.md. Turning one on is a decision, not a deploy side effect.

Customer data, telemetry and secrets never go in git. Pull sample data from S3 into a gitignored folder, and keep secrets in the environment or the secret store.

## Contact

Cody Inman, Director of Technology. Open an issue on the repo in question for anything else.
