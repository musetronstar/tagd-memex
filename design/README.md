# tagd:memex Design Process

The design derives from Vannevar Bush's seminal essay "As We May Think," which
describes the memex:

    ../docs/As_We_May_Think-Vannevar_Bush-Atlantic_magazine-original.pdf

The 1945 vision will be realized as a tagd app.
This document defines the methodology of the tagd:memex design process.

## 1. Analytical Units

Each analytical unit will be derived from index card photographs in

    analytical-units-index-cards/

and written (completed and edited) to the file

    analytical-units.md

All source passages were selected from sections 6 and 7 of Bush's essay and
marked on this image:

- [Marked source passages (sections 6–7)](analytical-units-index-cards/20260916_124823.jpg)

* Quote the published essay exactly in each **Source Passage**.
* Use ellipses or square brackets transparently when shortening a passage.
* Treat wording on the index cards as design notes.
* Place paraphrase or interpretation in **Design Interpretation**, not inside the quotation.

An encircled **sequence number** appears in the margin beside each passage
selected for an analytical unit.

Each analytical-unit index card carries the corresponding encircled sequence
number in its top-right corner, on both front and back when applicable.

This is the index card template:

- [Analytical-unit index card template](analytical-units-index-cards/20260916_125224.jpg)

Some index cards are sparse and require completion and editing.
Each analytical unit centers on one primary user affordance and separates required
tagd:memex behavior from implementation details.

All substantive card content is captured during the initial transcription.
Implementation-specific decisions and constraints are preserved under
**Implementation Notes** for incorporation into later software specifications.

The encircled number identifies the source. Multiple card images may support one analytical unit,
and distinct affordances from the same source use lowercase suffixes such as `03a` and `03b`.

### Analytical Unit File Sections

`analytical-units.md` will have a section for each analytical unit
with a heading in the form:

    ## <zero-padded-two-digit-sequence-number-and-optional-suffix> — <component-classes>: <abbreviated-affordance>

### Analytical Unit File Format

    Index Card Sources
        ↓ preserve design provenance for
    Source Reference
        ↓ locates
    Source Passage
        ↓ describes
    Bush Concept or Mechanism
        ↓ inspires
    Design Interpretation
        ↓ classified by
    Component Classes: Storage | Input | View | Control
        ↓ supports
    Affordance (to the user)
        ↓ requires
    Capabilities (by the system)
        ↓ realized through
    Behaviors
        ↓ constrained by
    Design Invariants
    Open Questions (only when unresolved)

Use an **Open Questions** subsection only when Socratic review leaves a design
issue unresolved. State the uncertainty and its consequence without presenting
speculation as a requirement. Remove the subsection after the issue is resolved
and incorporate the decision into the appropriate fields.

---

#### Example

The following example is an illustrative draft. It demonstrates the format but
does not establish authoritative requirements. The completed analytical units
and user stories become authoritative only after review.

```markdown
## 02 — View: View a Record

### Index Card Sources

- [02 — View: View a Record (front)](analytical-units-index-cards/20260916_125400.jpg)
- [02 — View: View a Record (back)](analytical-units-index-cards/20260916_125408.jpg)

### Source Reference

Vannevar Bush, "As We May Think," section 6.

### Source Passage

> On the top are slanting translucent screens, on which material can be
> projected for convenient reading.

### Bush Concept or Mechanism

Translucent screen

### Design Interpretation

A viewable region in a web interface that can present a record.

### Component Classes

View

### Affordance

A user can view a presented record.

### Capabilities

The view is composable and can present

1. a single record; or
2. a composite of several other views in a fractal (self-similar and recursive)
   structure.

### Behaviors

When a record is requested for presentation, the view presents that record.

If the record is a composite containing other records, those records will
be presented as views within the containing view.

### Implementation Notes

The `httagd` app has a template `memex/view.html.tpl` and a handler function
that produces HTML output of a record (single or composite/fractal).

URL format:

    /<record>?v=memex/view.html

Where `<record>` is the tag `_id` representing the memex record.

### Design Invariants

The view presents the requested record.

```

## 2. User Stories

User stories will be captured in the file

    user-stories.md

Use the narrowest role that materially changes a story's goal or permitted
behavior. Use the generic role **user** for capabilities shared by all roles.
Assign each story a stable, globally unique identifier in the form `US-###`.
Identifiers do not change when stories are regrouped or reprioritized.

The file sections will be grouped by

### Priority

1. **High** (must have first for prototype)
2. **Medium** (needed for functional application)
3. **Low** (nice to have—added touches and customizations but non-essential)

### Component Classes (one or more)

- **Storage**
- **Input**
- **View**
- **Control**

With headings in the form:

    ## <priority> Priority — <component-classes> User Stories

Example:

    ## High Priority — Storage User Stories

Combined example:

    ## Medium Priority — View + Control User Stories

The **Analytical Units** subsection will reference one or more exact
corresponding section titles in the `analytical-units.md` file. Traceability is
maintained one-way from user stories to analytical units; analytical units do
not maintain duplicate lists of user-story references.

Each acceptance scenario uses
* **Given** for the relevant starting state.
* **When** for one user action or triggering event.
* **Then** for one or more observable outcomes.

A story may contain multiple scenarios for alternatives, validation failures, or
edge cases. Include interface details only when the design explicitly requires them.

### User Story File Example

This example is also an illustrative draft rather than an authoritative
requirement.

```markdown
## High Priority — Storage User Stories

### US-001 Store Record Options

#### Analytical Units

- 03 — Input: Store Record

#### User Story

As a user,  
I want to choose whether to add a file record or a text record,  
so that I can store either kind of content.

#### Acceptance Criteria

**Given** that I am on the **desk view**  
**When** I select **Add Record**  
**Then** I am presented with two options:

1. Add file.
2. Add text.

### US-002 Store File Record

#### Analytical Units

- 03 — Input: Store Record

#### User Story

As a user,  
I want to store a file record,  
so that my file is available for future access.

#### Acceptance Criteria

**Given** that I am viewing the add-record options  
**When** I select **Add File**  
**Then** a file-selection dialog opens  
**And** I can choose a file from my device.
```
