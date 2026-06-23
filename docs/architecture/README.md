# docs/architecture/

In-depth system design documents.

## Purpose

Architecture documents provide detailed explanations of how specific parts of Build Better OS work — data models, service interactions, flow diagrams, and design rationale. Unlike ADRs (which record decisions), architecture documents describe the current design in depth.

## Folder Structure

```
architecture/
└── README.md     ← this file
```

Design documents will be added as systems are designed and built.

**Expected future documents:**
```
architecture/
├── content-lifecycle.md      ← how a content piece moves from draft to archive
├── event-model.md            ← event types, schemas, and flow
├── service-topology.md       ← service map and communication patterns
└── data-model.md             ← core entity relationships
```

## What Belongs Here

- Service interaction diagrams
- Data model documentation
- Sequence diagrams for complex workflows
- Deep dives on specific system behaviors
- Trade-off analyses for significant design choices

## What Does NOT Belong Here

- Decision records (those belong in `docs/adr/`)
- How-to guides (those belong in `docs/guides/`)
- Code-level documentation (that belongs alongside the code)
- High-level system overview (that lives in root `ARCHITECTURE.md`)

## Document Format

Architecture documents should:
- Have a clear title and purpose statement at the top
- Include a date of last significant revision
- Use diagrams (ASCII or linked images) where structure is easier to see than describe
- Link to relevant ADRs for decision context
- Note where the document may be outdated and what to check

## Relationships

- Architecture docs **elaborate on** the overview in root `ARCHITECTURE.md`
- Architecture docs **reference** decisions recorded in `docs/adr/`
- Architecture docs **describe** systems implemented in `services/` and `platform/`

## Future Extensions

- Automated architecture diagram generation
- Living architecture docs generated from service interfaces
