# tagd:memex design process

The design is derived from Vannevar Bush's seminal essay "As We May Think"
which describes the memex (the memex essay):

    ../docs/As_We_May_Think-Vannevar_Bush-Atlantic_magazine-original.pdf

The 1945 vision will be realized as a tagd app.
This contains the methodology of the tagd:memex design process.

## 1. Analyitical Units

### Analyitical Unit Files

In the form:

    analytical-units/<sequence-number>-<component>-<slugified-abbreviated-affordance>.md

Example:

    analytical-units/01-view-compare-records.md

Where the sequence number is the from the order in from which
the source passage was derived in the the memex essay.

### Analyitical Unit File Format

    Source passage
        ↓ describes
    Physical Mechanism
        ↓ decomposes
    General Component: Storage | Input | View | Control
        ↓ categorizes
    Affordances (to the user)
        ↓ requires
    Capabilities (by the system)
        ↓ realized through
    Behaviors
        ↓ eventually tested by
    Acceptance Criteria

---

#### Example

```markdown
# 02 View that Presents Records

## Source Passage

> translucent screens, on which material can be projected for convenient reading

## Physical Mechanism

Translucent screen

## General Component

View

## Affordance

A viewable area that presents a record to a user.

## Capabilities

The view is composable and can present

1. a single record
2. or a composite of several other views in a fractal way (self-similar and recursive).

The `httagd` app has a template `memex/view.html.tpl` and a handler function
that produces HTML output of a record (single or composite/fractal).

## Behaviors

When an HTTP request for a view occurs, that TAGL subject (which should be a record)
will be returned (HTTP response) as an HTML partial.

If the record is a composite containing other records, those records will
be produced as HTML partials in the containing view using the same
template and handler.

URL format:

    /<record>?v=memex/view.html

Where `<record>` is the tag `_id` representing the memex record.

## Acceptance Criteria

When a well formed URL is requested, the correct HTML output is returned
with an HTTP status of 200.
```

## 2. User Stories

User story files will contain multiple user stories grouped by

* Priority: **1. High** | **2. Medium** | **3. Low**
* General Component: **Storage** | **Input** | **View** | **Control**

### User Story Files

In the form:

    user-stories/<priority-number>-<component>.md

Example:

    analytical-units/1-storage.md

### User Story File Example

```markdown
# High Priority Storage User Stories

## 1. Store Record Options

### Analytical Unit

    analytical-units/03-input-store-record.md

### User Story

As a user
I want to have the option to choose store a file or text record
So that I can store a file or a text

### Acceptance Criteria

**Given** that I am on the **desk view**, I see an "add record" icon.
**When** I touch/click the icon,
**Then** I am presented two options
1. Add file.
2. Add text.

## 2. Store File Record

### Analytical Unit

    analytical-units/03-input-store-record.md

### User Story

As a user
I want to store a file record
So that my file is available for future access.

### Acceptance Criteria

Given that I see the add file option
When I click the option, I am presented an upload file dialogue
Then I can browse my device storage to and choose the file I want to upload.
```

