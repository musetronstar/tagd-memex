# tagd:memex User Stories

This document contains the reviewed user stories derived from
`analytical-units.md`.

Stories are grouped by priority and component classes according to
`design/README.md`. Each story has a stable `US-###` identifier and references
the exact analytical-unit titles from which it was derived.

## High Priority — View + Control User Stories

### US-001 Work from a Composite Desk

#### Analytical Units

- 01 — View + Control: Work from a Composite Desk

#### User Story

As a user,  
I want search, navigation, Record Views, and record controls in one composite
Desk,  
so that I can find, view, and act upon records from one coherent workspace.

#### Acceptance Criteria

##### Scenario: Present the Desk on a wide viewport

**Given** that I am using a wide viewport  
**When** I open the Desk  
**Then** Record Search is presented across the top  
**And** tagspace navigation is presented on the left  
**And** the record workspace is presented in the main area  
**And** the available record actions remain associated with the Record Views
they operate upon.

##### Scenario: Present the Desk on a narrow viewport

**Given** that I am using a narrow viewport  
**When** I open the Desk  
**Then** Record Search and tagspace navigation can be collapsed  
**And** the active Record View is presented first  
**And** an association counterpart, when present, is available immediately
below it in collapsed form  
**And** record actions remain associated with the records they operate upon.

##### Scenario: Preserve the Desk as one workspace

**Given** that the Desk contains several Views and controls  
**When** one contained View changes state  
**Then** the Desk continues to present the contained elements as one coherent
workspace.

### US-002 Open a Record Without Losing the Previous Record

#### Analytical Units

- 01 — View + Control: Work from a Composite Desk

#### User Story

As a user,  
I want a record I open to become active without losing the previous record,  
so that I can explore records while preserving my immediate working context.

#### Acceptance Criteria

##### Scenario: Promote an opened record

**Given** that one record is primary and active  
**When** I open another record through a navigation action  
**Then** the opened record becomes primary and active  
**And** the previous record remains immediately available in the secondary
position or RecordStack  
**And** the association and trail feed follows the newly active record  
**And** the navigation is recorded in browser history.

##### Scenario: Return to the previous workspace

**Given** that I promoted another record from the current workspace  
**When** I use Browser Back  
**Then** the previous primary and secondary record context is restored  
**And** the previous trail context is restored  
**And** the previous reading position is restored when available.

##### Scenario: Open an unrelated record

**Given** that one record is active  
**And** another record has no association with it  
**When** I open the unrelated record  
**Then** the unrelated record becomes primary and active  
**And** no association is created between the records  
**And** the records are not assigned Source and Target roles merely because
one followed the other.

### US-020 Work with Source and Target Views

#### Analytical Units

- 12 — View + Control: Work with Source and Target Views

#### User Story

As a user,  
I want to inspect and act on related records while keeping their relationship
visible,  
so that I can work with an association without losing sight of its direction.

#### Acceptance Criteria

##### Scenario: Present Source and Target side by side on a wide viewport

**Given** that I am viewing an association on a wide viewport  
**When** the workspace is presented  
**Then** Source appears on the left and Target on the right  
**And** both Views can be expanded  
**And** only one View receives active commands.

##### Scenario: Stack the pair on a narrow viewport

**Given** that I am viewing an association on a narrow viewport  
**When** the workspace is presented  
**Then** the active View is expanded first  
**And** the counterpart is retained as a collapsed View immediately below it.

##### Scenario: Promote the collapsed counterpart on a narrow viewport

**Given** that a counterpart is collapsed below the active View on a narrow
viewport  
**When** I activate the collapsed counterpart  
**Then** it is promoted to the first position and expanded  
**And** the former active View collapses immediately beneath it  
**And** the Source and Target roles do not change.

##### Scenario: Indicate the active View

**Given** that one View is active  
**When** the workspace is presented  
**Then** the active View is indicated with a contrasting border, a visible
non-color cue, and an accessible state  
**And** active state is not conveyed by color alone.

##### Scenario: Preserve association direction independent of focus and layout

**Given** that an association has a direction  
**When** focus or layout changes  
**Then** persistent Source and Target labels, direction arrows, and relationship
text preserve the actual direction  
**And** direction is not inferred solely from left/right position.

### US-021 Load a Record into a View

#### Analytical Units

- 12 — View + Control: Work with Source and Target Views

#### User Story

As a user,  
I want to load records into the Views of the workspace,  
so that I can choose which records I am working with.

#### Acceptance Criteria

##### Scenario: Load a record into an empty View

**Given** that a View is empty  
**When** the View is presented  
**Then** it presents a prominent Load Record control.

##### Scenario: Load a record into a loaded active View

**Given** that the active View already has a record loaded  
**When** I use its Load Record action  
**Then** Record Search opens.

##### Scenario: Opening a result updates the active record and feed

**Given** that I open a result from Load Record's search  
**When** the record loads  
**Then** it follows the shared promotion behavior  
**And** the association and trail feed updates to the newly active record.

##### Scenario: Activation focuses navigation, not input

**Given** that I activate a Record View  
**When** it becomes active  
**Then** it is focused for navigation  
**And** no input is focused by activation or expansion alone.

##### Scenario: Opening an input task focuses its default input

**Given** that I open an input task such as Load Record, Record Search, or Add
Record  
**When** the task opens  
**Then** its contextual default input is focused.

### US-023 Associate Two Records

#### Analytical Units

- 14 — View + Control: Associate Two Records
- 06 — Input + Control: Add a Record
- 01 — View + Control: Work from a Composite Desk
- 12 — View + Control: Work with Source and Target Views

#### User Story

As a user,  
I want to connect two records with a named, directed association and inspect its
direction before saving,  
so that I can tie related records together.

#### Acceptance Criteria

##### Scenario: Start an association from a record

**Given** that I click Add Association on a record, whether primary or secondary  
**When** the Associate action opens  
**Then** that record supplies the initial source  
**And** record selection opens to choose the counterpart.

##### Scenario: Present both endpoints with direction

**Given** that I have selected the counterpart through Record Search  
**When** the association form is presented  
**Then** both endpoint records are shown  
**And** arrows and labels show the pending direction.

##### Scenario: Name the association and adjust its identifier

**Given** that I am completing the association form  
**When** I enter an association title  
**Then** an editable proposed unique ID is shown  
**And** I can adjust it before saving.

##### Scenario: Reverse the direction

**Given** that the association form shows a pending direction  
**When** I reverse it  
**Then** `_from` and `_to` are swapped  
**And** each anchor's endpoint designation is updated so it still refers to the
same record.

##### Scenario: Selecting endpoints does not store the association

**Given** that I have selected both endpoints  
**When** I have not submitted Associate  
**Then** no association is stored.

##### Scenario: Persist the association on explicit submission

**Given** that I have reviewed the title, proposed ID, direction, and any
anchors  
**When** I submit Associate  
**Then** the association is stored  
**And** its identity is independent of the endpoint records' identities.

##### Scenario: Create a new endpoint without leaving the association form

**Given** that I am in the Add Association workflow  
**When** I use Add Record to create an endpoint  
**Then** the created endpoint is returned to the association form  
**And** saving the association remains a separate action  
**And** cancelling the association form does not undo an endpoint already stored.

### US-027 Browse a Record's Associations and Trails

#### Analytical Units

- 15 — View + Control: Browse a Record's Associations and Trails

#### User Story

As a user,  
I want the active record's associations and participating trails presented,  
so that I can discover connected records and enter trails.

#### Acceptance Criteria

##### Scenario: Present the feed for the active record

**Given** that a record is active  
**When** it is presented  
**Then** its associations are shown in distinguishable incoming and outgoing
groups with direction labels  
**And** each group orders its entries by association tag rank  
**And** trails in which the active record participates are listed.

##### Scenario: Show bounded previews with independent Load more

**Given** that a direction group has many associations  
**When** the feed is presented  
**Then** a bounded preview batch is shown  
**And** each direction group has its own Load more control.

##### Scenario: Open the other endpoint from an association preview

**Given** that an association preview is shown  
**When** I use its prominent endpoint link  
**Then** the other endpoint opens, the `_to` endpoint for an outgoing
association or the `_from` endpoint for an incoming association  
**And** the opened record is promoted, the previous record is retained, and
Browser Back restores the previous workspace.

##### Scenario: Open the association record itself

**Given** that an association preview is shown  
**When** I use the smaller, consistently displayed Open association icon  
**Then** the association record itself opens  
**And** the opened record is promoted, the previous record is retained, and
Browser Back restores the previous workspace.

##### Scenario: Navigation does not require inspecting first

**Given** that an association preview is shown  
**When** I open a record  
**Then** I can open it directly without an inspect-then-open sequence  
**And** expanded metadata remains available to reveal more detail.

##### Scenario: The feed follows the active record

**Given** that I promote a different record  
**When** it becomes active  
**Then** the association and trail feed updates to follow the newly active
record.

### US-030 Browse a Web of Trails

#### Analytical Units

- 18 — View + Control: Browse a Web of Trails

#### User Story

As a user,  
I want to follow trail connections and move onto another trail at a shared record
without losing my place,  
so that I can explore a web of trails and take side excursions.

#### Acceptance Criteria

##### Scenario: Show the current trail and its continuations

**Given** that I am browsing a trail  
**When** a record is presented in trail context  
**Then** the current trail and its available connected continuations are shown  
**And** overlapping trails at shared records are indicated.

##### Scenario: Choose a continuation at a junction

**Given** that I am at a junction  
**When** a selected route does not already determine the next step  
**Then** I choose among the connected continuations  
**And** membership rank orders the choices but never fabricates a next edge.

##### Scenario: Follow a determined route

**Given** that a selected route determines the next step  
**When** I continue  
**Then** the next step follows that route.

##### Scenario: Switch to another trail at a shared record

**Given** that I am at a record shared by multiple trails  
**When** I select another trail  
**Then** the trail name, continuations, and navigation context change  
**And** the current record stays active  
**And** it does not jump to the new trail's trailhead.

##### Scenario: Go to trailhead is explicit

**Given** that I am browsing a trail  
**When** I choose Go to trailhead  
**Then** I am taken to the selected trail's entry record.

##### Scenario: Browsing an association in reverse preserves its direction

**Given** that I follow an association in reverse  
**When** the record is presented  
**Then** the association's semantic direction is preserved  
**And** labels and arrows make the distinction clear.

##### Scenario: Browser Back restores the arrival route and context

**Given** that I have navigated and switched trail context  
**When** I use Browser Back  
**Then** the prior context and actual arrival route are restored.

### US-031 Open a Trail at Its Trailhead

#### Analytical Units

- 19 — View + Control: Open a Trail at Its Trailhead
- 08a — View: Present Search Results

#### User Story

As a user,  
I want to find a trail and begin at its consistent entry point,  
so that I can start a trail from a predictable place.

#### Acceptance Criteria

##### Scenario: Open a trail from search at its trailhead

**Given** that I find a trail record through search  
**When** I use the default trail-navigation action without a more specific entry
location  
**Then** the trail's designated entry record loads with that trail's context
active  
**And** the opened record follows the shared promotion and history behavior.

##### Scenario: Trailhead is independent of membership order and creation time

**Given** that a trail has a stored trailhead  
**When** memberships are reordered  
**Then** the trailhead does not change  
**And** it is not recomputed from membership order or record creation time.

##### Scenario: Enter through a specific record without redefining the trailhead

**Given** that I enter a trail through a specific shared record or a direct link  
**When** the record loads in trail context  
**Then** it need not visit the trailhead  
**And** the trailhead is not redefined.

##### Scenario: Change the designated entry record deliberately

**Given** that I want a different entry record  
**When** I deliberately change the designated trailhead  
**Then** the trail's entry record is updated.

## High Priority — View User Stories

### US-003 View a Record

#### Analytical Units

- 02 — View: View a Record

#### User Story

As a user,  
I want to view the content of a record I open,  
so that I can read or otherwise consume its material.

#### Acceptance Criteria

##### Scenario: Present an ordinary record

**Given** that I have opened an ordinary (non-composite) record  
**When** its View is presented  
**Then** the View presents that record's content  
**And** the record is presented through the same View abstraction used for
every record kind, with rendering appropriate to its kind.

### US-014 Present and Open Search Results

#### Analytical Units

- 08a — View: Present Search Results

#### User Story

As a user,  
I want search results presented so I can recognize matches and open the intended
record,  
so that I can retrieve the record I was looking for.

#### Acceptance Criteria

##### Scenario: Present recognizable results

**Given** that a search has returned results  
**When** the results are presented  
**Then** each result shows the record's identity, a media-type icon or a
thumbnail where it aids recognition, and a snippet with matching terms
emphasized.

##### Scenario: Distinguish exact matches from recommendations

**Given** that results include exact matches and high-confidence recommendations  
**When** the results are presented  
**Then** exact matches appear in a distinct header region  
**And** recommendations are shown with a different label  
**And** a recommendation is never labeled as an exact match.

##### Scenario: Order results by relevance

**Given** that results are presented below the header region  
**When** they are ordered  
**Then** they are ranked by relevance to the complete query  
**And** tag rank serves as a ranking signal and a deterministic tie-breaker.

##### Scenario: Open a result

**Given** that results are presented  
**When** I open a result  
**Then** the record becomes primary and active  
**And** the previous active record is retained in the secondary position or
RecordStack  
**And** standard browser link actions, such as opening in a new tab, are
preserved  
**And** Browser Back restores the previous workspace.

##### Scenario: Selecting a result as form data is distinct from opening it

**Given** that I am selecting a record as form data, such as an association
endpoint  
**When** I select a result  
**Then** it is selected for that form  
**And** it is not opened for navigation.

## High Priority — Input User Stories

### US-005 Enter and Edit Multiline Text

#### Analytical Units

- 03 — Input: Enter Text

#### User Story

As a user,  
I want to enter and edit multiline Unicode text,  
so that I can compose the textual content of a record.

#### Acceptance Criteria

##### Scenario: Retain text while editing

**Given** that I am entering text in a multiline text control  
**When** I type and edit the text  
**Then** the control reflects and retains the current value until the containing
workflow is submitted or cancelled.

##### Scenario: Preserve Unicode and line breaks

**Given** that I enter UTF-8 characters and intentional line breaks  
**When** I review the entered text  
**Then** the Unicode characters are preserved  
**And** the intentional line breaks are preserved.

##### Scenario: Enter inserts a newline in multiline text

**Given** that I am editing a multiline text control  
**When** I press Enter  
**Then** a newline is inserted  
**And** the text is not submitted.

##### Scenario: Submit deliberately

**Given** that I have entered text in a multiline control  
**When** I activate the visible Submit control, or press Ctrl+Enter or
Command+Enter  
**Then** the containing workflow is submitted  
**And** entering or editing text alone did not create or store a record.

## High Priority — Control User Stories

### US-006 Trigger an Operation with a Control

#### Analytical Units

- 04 — Control: Trigger an Operation

#### User Story

As a user,  
I want to trigger operations through visible controls or equivalent keyboard
shortcuts,  
so that I can deliberately invoke memex operations.

#### Acceptance Criteria

##### Scenario: Activate a control

**Given** that a control for an available operation is presented  
**When** I activate it by mouse, touch, or keyboard  
**Then** the system performs that control's associated operation  
**And** the same operation results regardless of which activation method I used.

##### Scenario: Use an equivalent keyboard shortcut

**Given** that an operation has both a visible control and a mapped keyboard
shortcut  
**When** I invoke the keyboard shortcut  
**Then** the system performs the same operation as the visible control.

##### Scenario: A control communicates its availability

**Given** that an operation is currently unavailable  
**When** its control is presented  
**Then** the control indicates it is unavailable  
**And** activating it does not perform the operation.

##### Scenario: An essential operation is reachable without a shortcut

**Given** that an operation is essential  
**When** I look for a way to invoke it  
**Then** a visible control is available  
**And** the keyboard shortcut is not the only means of invoking it.

## High Priority — Storage User Stories

### US-007 Store a Record for Later Retrieval

#### Analytical Units

- 05 — Storage: Store Records

#### User Story

As a user,  
I want the records I create to be stored,  
so that I can retrieve and use them later.

#### Acceptance Criteria

##### Scenario: Store a text-only record

**Given** that I store a text-only record  
**When** the store operation completes  
**Then** the record's text content is durably retained in the tagspace as a TAGL
object value  
**And** it can be retrieved later through its tagspace identity.

##### Scenario: Store a file-backed record

**Given** that I store a file-backed record  
**When** the store operation completes  
**Then** Filepile durably stores the file content in the filesystem  
**And** the record's semantic representation is retained in the tagspace  
**And** both can be retrieved later through the record's tagspace identity.

##### Scenario: Retrieve a stored record

**Given** that a record was previously stored  
**When** I retrieve it through its tagspace identity  
**Then** the stored record and its content are returned.

## High Priority — Input + Control User Stories

### US-008 Add a Record

#### Analytical Units

- 06 — Input + Control: Add a Record

#### User Story

As a user,  
I want to add a text record, one or more file records, or a text record with
file attachments,  
so that I can store new material in the memex.

#### Acceptance Criteria

##### Scenario: Provide a title and adjust the proposed identifier

**Given** that I am adding a record  
**When** I enter a required title  
**Then** the system derives an editable candidate record identifier from it  
**And** I can adjust that identifier before storing.

##### Scenario: Add a text-only record

**Given** that I have entered text and selected no files  
**When** I submit the Add Record form  
**Then** one text record is stored  
**And** the stored record is presented in a View.

##### Scenario: Add one or more file records

**Given** that I have selected one or more files and entered no text  
**When** I submit the Add Record form  
**Then** one file record is stored for each file.

##### Scenario: Add a text record with file attachments

**Given** that I have entered text and selected one or more files  
**When** I submit the Add Record form  
**Then** one text record is stored  
**And** one file record is stored for each file  
**And** each file record is connected to the text record by an attachment
association.

##### Scenario: Validate before storing

**Given** that the proposed records are invalid  
**When** I submit the Add Record form  
**Then** the system reports the validation problem  
**And** no records are stored.

##### Scenario: A later step fails without rolling back earlier changes

**Given** that I submitted an Add Record form that creates several records  
**And** an earlier record was stored successfully  
**When** a later step fails  
**Then** the earlier successful changes remain  
**And** the system displays the returned HTTP status and raw TAGL errors  
**And** the failure does not imply that the whole operation was rolled back.

### US-011 Search for Records

#### Analytical Units

- 08 — Input + Control: Search for Records

#### User Story

As a user,  
I want to find records by entering search terms and submitting the search,  
so that I can locate the records I need.

#### Acceptance Criteria

##### Scenario: Run a search on explicit submission

**Given** that I have entered search terms  
**When** I select Search or press Enter in the search input  
**Then** the search runs  
**And** the matching records are presented.

##### Scenario: Editing a query does not execute it

**Given** that I am editing the search query  
**When** I change the query without submitting  
**Then** the search does not run.

##### Scenario: A submitted search is recorded in browser history

**Given** that I have submitted a search  
**When** the results are presented  
**Then** the submitted search is recorded in browser history  
**And** using Browser Back restores the preceding search state.

##### Scenario: A search has a stable, shareable URL

**Given** that I have submitted a search  
**When** I bookmark or share its URL  
**Then** revisiting the URL reproduces the query rather than a frozen snapshot of
its earlier results.

##### Scenario: Searching does not change stored records

**Given** that I run a search  
**When** the results are presented  
**Then** no stored records are changed.

### US-028 Create a Named Trail

#### Analytical Units

- 16 — Input + Control: Create a Named Trail

#### User Story

As a user,  
I want to create and name a trail beginning with one association,  
so that I can save a named, connected collection of associations I can follow
again.

#### Acceptance Criteria

##### Scenario: Create a trail from one association

**Given** that I have selected an association and a traversal direction  
**When** I name the trail and save it  
**Then** the trail is created with a unique identity  
**And** it is saved with that one association  
**And** the initial trailhead is the starting endpoint of the first
association's chosen traversal direction, stored explicitly.

##### Scenario: Extend later rather than requiring a second association

**Given** that I have saved a trail with one association  
**When** I finish  
**Then** the trail is valid without a second association  
**And** I can return later and use Extend trail  
**And** as it is extended the trail may branch, rejoin, or contain cycles rather
than remaining a single linear path.

##### Scenario: Rank candidates are suggestions, not connections

**Given** that I am searching associations or drilling down for candidate
extensions  
**When** rank-related candidates are offered  
**Then** they are discovery suggestions only  
**And** membership requires actual endpoint connectivity  
**And** the system does not silently infer an association from overlapping ranks.

##### Scenario: Creation does not copy or reparent associations

**Given** that I create a trail from an existing association  
**When** the trail is saved  
**Then** the association is neither copied nor reparented.

### US-029 Extend a Trail

#### Analytical Units

- 17 — Input + Control: Extend a Trail
- 16 — Input + Control: Create a Named Trail

#### User Story

As a user,  
I want to extend an existing trail or include an association in another trail,  
so that I can build up connected trails incrementally.

#### Acceptance Criteria

##### Scenario: Extend at any participating record

**Given** that I select a participating record of a trail  
**When** I use Extend trail  
**Then** I can extend from that record, including at branches and rejoins.

##### Scenario: Add a connected association as membership

**Given** that I am extending a trail at a chosen record  
**When** I select an existing connected association or create a connecting
association  
**Then** the added membership connects to the current trail by endpoint identity.

##### Scenario: Rank discovery candidates do not create connections

**Given** that rank-based discovery candidates are offered separately from direct
connections  
**When** I review them  
**Then** I explicitly choose the continuation  
**And** rank discovery does not create a connection on its own.

##### Scenario: Add an association to a new or connected existing trail

**Given** that I am adding an association to a trail  
**When** I choose the target trail  
**Then** I can add it to a new trail or to a connected existing trail.

##### Scenario: Shared associations are not copied or reparented

**Given** that an association belongs to multiple trails  
**When** I add or remove a trail membership  
**Then** the association itself is neither copied nor reparented  
**And** removing a membership removes that trail's reference, not the
association.

## Medium Priority — View User Stories

### US-004 View a Composite Record

#### Analytical Units

- 02 — View: View a Record

#### User Story

As a user,  
I want an explicitly composite record to present the records it contains,  
so that I can see the whole composite in one place.

#### Acceptance Criteria

##### Scenario: Present contained records as child Views

**Given** that I open an explicitly composite record  
**When** its View is presented  
**Then** each record it explicitly contains is presented as a child View within
the containing View.

##### Scenario: Nested composites render recursively

**Given** that a composite record contains another composite record  
**When** the outer composite is presented  
**Then** the inner composite is itself presented as a containing View with its
own child Views.

##### Scenario: An association is not expanded as containment

**Given** that I open a record that has associations to other records  
**When** its View is presented  
**Then** the associated records are not automatically presented as contained
child Views  
**And** those associations remain reachable through the association feed rather
than through visual containment.

### US-009 Recognize and Render a Record by Media Type

#### Analytical Units

- 06a — View: Recognize a Record's Media Type

#### User Story

As a user,  
I want to recognize a record's broad media type and view it through an
appropriate default presentation,  
so that I can identify and consume different kinds of content.

#### Acceptance Criteria

##### Scenario: Show a media-type icon when a file record is added

**Given** that I add a file-backed record  
**When** the system determines its effective presentation specialization  
**Then** the record displays the corresponding media-type icon.

##### Scenario: Render a supported media type with its default View

**Given** that a file-backed record has a supported presentation specialization,
such as document, image, audio, or video  
**When** I view the record  
**Then** the specialization selects the default renderer for that type.

##### Scenario: Fall back to a binary presentation for unsupported content

**Given** that no supported specialization can be determined for a file-backed
record  
**When** I view the record  
**Then** the record uses the binary fallback presentation  
**And** it remains available for download or external handling  
**And** a link is offered to report the unsupported type.

##### Scenario: Semantic tags remain independent of the presentation specialization

**Given** that a record has an effective presentation specialization  
**When** I add flexible semantic tags to it  
**Then** those tags describe the record independently  
**And** they do not change the default renderer.

##### Scenario: User actions do not change detected media type

**Given** that a file-backed record has a system-detected MIME or content type  
**When** I add or remove semantic tags, edit the record's title or other
predicates, or annotate or associate the record  
**Then** the detected MIME or content type is not altered by those actions.

### US-024 Read and Review Error Messages

#### Analytical Units

- 14a — View: Read and Review Error Messages

#### User Story

As a user,  
I want to recognize an error, correct its cause when possible, and review its
details later,  
so that I can understand and respond to failures.

#### Acceptance Criteria

##### Scenario: Show a validation error beside its input

**Given** that an input fails validation  
**When** the error is presented  
**Then** it is shown beside the relevant input.

##### Scenario: Show a non-validation failure in a persistent error region

**Given** that an operation fails for a reason other than input validation  
**When** the error is presented  
**Then** it is shown in a persistent error region.

##### Scenario: Show service-error details

**Given** that a service request fails  
**When** its error is presented  
**Then** the persistent error region displays the returned HTTP status and the
raw TAGL response.

##### Scenario: Preserve entered data on failure

**Given** that an operation fails  
**When** the error is shown  
**Then** my entered data is preserved.

##### Scenario: An actionable error stays until resolved or explicitly dismissed

**Given** that an error requires correction  
**When** I click outside it  
**Then** it is not dismissed  
**And** it remains visible until resolved or explicitly dismissed.

##### Scenario: Dismissing an error does not erase its history or imply success

**Given** that I dismiss a visible error  
**When** it is closed  
**Then** its retained event history is not erased  
**And** dismissal does not imply the failed operation succeeded  
**And** failure does not imply rollback of earlier successful changes.

## Medium Priority — Input + Control User Stories

### US-012 Refine a Search with Facets and Tagspace Browsing

#### Analytical Units

- 08 — Input + Control: Search for Records

#### User Story

As a user,  
I want to refine a search using facets and by browsing the tagspace,  
so that I can constrain what I am looking for without knowing the query language.

#### Acceptance Criteria

##### Scenario: Refine with "What is it?" and "How is it related?" facets

**Given** that I am building a search  
**When** I select facet values grouped as "What is it?" and "How is it related?"  
**Then** the facets are combined with any full-text terms into the query  
**And** I am not forced through a fixed wizard sequence.

##### Scenario: Browse the tagspace to select query parts

**Given** that I am building a search  
**When** I browse the tagspace and select a tag  
**Then** the selection becomes a tag-valued part of the same query state.

##### Scenario: Build a query without typing TAGL

**Given** that I build a query using facets and tagspace browsing  
**When** I submit it  
**Then** the selections are translated into a TAGL query  
**And** the query is composed entirely through the facet and tagspace-browser
controls, requiring no TAGL to be typed.

##### Scenario: Filter results by a media-type facet

**Given** that media-type facets are represented among search results  
**When** I select a media-type facet  
**Then** a query filter is added  
**And** the filtered search follows explicit submission.

### US-016 Retrieve Records by Referent

#### Analytical Units

- 09 — Input + Control: Retrieve Familiar Records

#### User Story

As a user,  
I want to find records by their TAGL referents as well as their tag IDs,  
so that I can retrieve familiar records by memorable names.

#### Acceptance Criteria

##### Scenario: Search by referent

**Given** that I enter a referent in search  
**When** I submit the search  
**Then** records are matched by referent as well as by tag ID.

##### Scenario: Resolve an exact referent in context

**Given** that my query resolves to an exact referent in the applicable context  
**When** the results are presented  
**Then** the exact referent match appears in the exact-match header  
**And** its context participates in determining the exact match.

## Medium Priority — View + Control User Stories

### US-015 Navigate Search Result Pages

#### Analytical Units

- 08b — View + Control: Navigate Search Result Pages

#### User Story

As a user,  
I want to move through a large result set and return to a prior position,  
so that I can review many results without losing my place.

#### Acceptance Criteria

##### Scenario: Navigate with numbered pages and Previous/Next

**Given** that results span more than one page  
**When** I select a numbered page or Previous/Next  
**Then** the displayed results page is replaced  
**And** the full query is preserved.

##### Scenario: Result pages have stable URLs

**Given** that I am on a result page  
**When** I bookmark or share its URL  
**Then** the URL retains the query and the page position.

##### Scenario: Return to a prior result position with Browser Back

**Given** that I have navigated across result pages  
**When** I use Browser Back  
**Then** my previous result position and navigation state are restored.

##### Scenario: Load more appends results when available

**Given** that the Load more enhancement is available  
**When** I select Load more  
**Then** another batch of results is appended  
**And** the query context and the history state needed to return to the
preceding position are preserved.

## Medium Priority — Control User Stories

### US-018 Navigate Within a Record

#### Analytical Units

- 10 — Control: Navigate Within a Record

#### User Story

As a user,  
I want to move through a multipage or flowing record in the active View,  
so that I can read or review its full content.

#### Acceptance Criteria

##### Scenario: Navigate content with keyboard, pointer, or touch

**Given** that a record is presented in the active View  
**When** I use keyboard, pointer, or touch navigation  
**Then** the View moves through the content in a manner appropriate to it  
**And** a paged format steps by page while flowing content scrolls by a
viewport-sized amount.

##### Scenario: Position is indicated

**Given** that I am navigating within a record  
**When** I move through it  
**Then** position is indicated through standard scroll or page controls.

##### Scenario: Record shortcuts do not capture input owned by a control

**Given** that focus is in a text field, text area, or editor within the record  
**When** I use keys that control that field  
**Then** those keys act on the focused control  
**And** record-navigation shortcuts do not capture that input.

##### Scenario: Navigation acts on the focused View

**Given** that multiple Views are present  
**When** I issue a record-navigation command  
**Then** it is routed to the focused active View.

##### Scenario: Browser history remains available

**Given** that I navigate within a record  
**When** I use standard browser Back and Forward  
**Then** browser history behavior remains available and distinct from in-record
navigation.

### US-019 Go to the Beginning of a Record

#### Analytical Units

- 11 — Control: Go to the Beginning of a Record

#### User Story

As a user,  
I want to return directly to the beginning of the active record,  
so that I can quickly restart my reading position.

#### Acceptance Criteria

##### Scenario: Go to the beginning of the active record

**Given** that I am partway through the active record  
**When** I activate Go to beginning, or its keyboard action for the active
renderer  
**Then** the active record moves to its beginning  
**And** no different record is loaded.

##### Scenario: Editable controls retain normal Home behavior

**Given** that focus is in editable text  
**When** I press Home  
**Then** Home behaves normally for that editable control  
**And** it is not globally intercepted to move the record.

## Medium Priority — Input + View User Stories

### US-022 Annotate a Record

#### Analytical Units

- 13 — Input + View: Annotate a Record

#### User Story

As a user,  
I want to add and view comments attached to a record or to a specific portion of
its content,  
so that I can record marginal notes and observations.

#### Acceptance Criteria

##### Scenario: Attach an annotation to a record

**Given** that I create annotation content as a record or select existing
content  
**When** I associate it with a record  
**Then** an association connects the annotation to the record  
**And** the annotation content and the association metadata have separate
identities.

##### Scenario: Anchor an annotation to a portion of content

**Given** that a renderer supports anchoring  
**When** I anchor the annotation to text, a page or image region, a media time
range, or a frame region  
**Then** the association stores the placement anchor and explicitly identifies
the anchored endpoint  
**And** direction or media type alone does not determine the anchored endpoint.

##### Scenario: Display supported annotations inline or marginally

**Given** that the renderer and viewport support annotation display  
**When** the annotated record is presented  
**Then** the annotation is displayed inline or in the margin.

##### Scenario: Expose the annotation at record level when its anchor cannot be interpreted

**Given** that the renderer cannot interpret an annotation's anchor  
**When** the record is presented  
**Then** the annotation remains available as an ordinary associated record.

##### Scenario: Reusing an annotation shares its content

**Given** that I reuse an existing annotation  
**When** it is used on another record  
**Then** the same content record is shared.

##### Scenario: An independently editable variation is a new record

**Given** that I want an independently editable variation of an annotation  
**When** I create it, optionally copied from a template or existing annotation  
**Then** it is a new record with provenance to its source  
**And** editing the copy does not alter its source  
**And** editing shared content affects its uses.

## Medium Priority — Control + View User Stories

### US-032 Share and Include Tagspace Content

#### Analytical Units

- 20 — Control + View: Share and Include Trails

#### User Story

As a user,  
I want to share tagspace content and include shared content in my current
tagspace,  
so that I can exchange memex material with others.

#### Acceptance Criteria

##### Scenario: Request a canonical tagspace dump

**Given** that I request a canonical TAGL tagspace dump through a `tagdurl`  
**When** the request succeeds  
**Then** a canonical TAGL representation of the tagspace is returned.

##### Scenario: Include TAGL from a URL

**Given** that remote include is enabled by system configuration  
**When** I include TAGL from a URL  
**Then** the supplied TAGL commands are executed against my current tagspace  
**And** existing duplicate handling, including `_ignore_duplicates`, is preserved  
**And** the destination is not required to be empty.

##### Scenario: Remote include can be disabled by system configuration

**Given** that remote include is disabled by system configuration  
**When** I attempt a remote include  
**Then** it is not available.

##### Scenario: Initial transfer carries TAGL only

**Given** that I dump or include content  
**When** the transfer completes  
**Then** tag and predicate definitions, file-record metadata and references, and
text stored in TAGL object values are included  
**And** file payload bytes, a complete Filepile backup, and guaranteed
destination file access are excluded.

##### Scenario: Partial failure does not roll back

**Given** that an include executes partway and then fails  
**When** the failure occurs  
**Then** earlier successful changes remain applied  
**And** the returned HTTP status and raw TAGL errors are displayed  
**And** no rollback is implied.

## Medium Priority — Input + Control + View User Stories

### US-034 Navigate Chronologies

#### Analytical Units

- 21 — Input + Control + View: Navigate Chronologies
- 16 — Input + Control: Create a Named Trail
- 17 — Input + Control: Extend a Trail
- 18 — View + Control: Browse a Web of Trails
- 19 — View + Control: Open a Trail at Its Trailhead

#### User Story

As a user,  
I want to supply domain-specific dates and browse records on a timeline by a
selected date type,  
so that I can follow a chronological account and select material from it.

#### Acceptance Criteria

##### Scenario: Supply a domain-specific date

**Given** that a record has a user-defined temporal type  
**When** I supply its date value  
**Then** the domain-specific date is stored on the record  
**And** it remains distinct from the system's creation and modification
timestamps.

##### Scenario: Browse records on a timeline for a selected date type

**Given** that I select a date type to govern the timeline  
**When** records are ordered  
**Then** matching records are ordered by their value for the selected date type
as a timeline  
**And** the interface clearly identifies which date type governs the current
timeline.

##### Scenario: Browse the Record Creation Timeline

**Given** that I select the record creation timestamp as the date type  
**When** records are ordered  
**Then** they are presented as the Record Creation Timeline.

##### Scenario: Only records with the selected date appear

**Given** that some records have no value for the selected date type  
**When** the timeline is presented  
**Then** only records possessing the selected date appear  
**And** no undated records are added and no other date is silently substituted.

##### Scenario: Browsing a timeline creates no associations or trail

**Given** that I browse a timeline  
**When** I move through the sequence  
**Then** no associations and no trail are created  
**And** a timeline is an ordered query view, not a trail  
**And** timeline adjacency creates neither an association nor a trail membership.

##### Scenario: Construct a named trail from selected material explicitly

**Given** that I want a trail from chronological material  
**When** I create it  
**Then** the named trail is created explicitly through the connected membership
model  
**And** creation timestamps do not define its connectivity.

## Low Priority — Input User Stories

### US-010 Select Files by Drag and Drop

#### Analytical Units

- 07 — Input: Select Files by Drag and Drop

#### User Story

As a user,  
I want to select files for a record by dragging and dropping them onto a drop
target,  
so that I can add files without using the file picker.

#### Acceptance Criteria

##### Scenario: Indicate a valid drop target

**Given** that I drag files over the Add Record form's drop target  
**When** the files are over the valid target  
**Then** the target provides clear visual feedback.

##### Scenario: Drop files to add them to the current selection

**Given** that I drag files over the valid drop target  
**When** I drop them on the target  
**Then** the files are added to the Add Record form's current file selection  
**And** they are represented using the same preview list as files chosen through
the file picker.

##### Scenario: Drag-and-drop and the file picker are equivalent

**Given** that I can select files either by drag and drop or by the file picker  
**When** I use either method  
**Then** both feed the same underlying file selection and the same subsequent
Add Record operation.

##### Scenario: Dropping outside the target does not add files or navigate away

**Given** that I drag files onto the page  
**When** I drop them outside the defined drop target  
**Then** the files are not added  
**And** the browser does not navigate away from tagd:memex.

##### Scenario: Selecting files does not store them

**Given** that I have selected files by drag and drop  
**When** I have not yet submitted the Add Record form  
**Then** the files are not stored  
**And** storage occurs only when I submit the form.

### US-035 Dictate Record Text by Voice

#### Analytical Units

- 03a — Input + Control: Dictate and Command by Voice

#### User Story

As a user,  
I want to dictate record text by voice,  
so that I can compose record content without typing.

#### Acceptance Criteria

##### Scenario: Dictate into a text field

**Given** that a microphone is available  
**And** I start voice dictation in a record text field  
**When** I speak  
**Then** my words are transcribed into the field's current value.

##### Scenario: Submission remains deliberate

**Given** that I have dictated text  
**When** I have not submitted  
**Then** no record is created  
**And** I submit the record deliberately.

##### Scenario: Fall back to the keyboard

**Given** that no microphone is present or permission is denied  
**When** I create a record  
**Then** the keyboard remains fully available for text entry.

##### Scenario: Voice capture requires an explicit start and shows listening

**Given** that I use voice dictation  
**When** voice capture is active  
**Then** it required an explicit start  
**And** a listening indicator is visible.

## Low Priority — Input + Control User Stories

### US-013 Enter an Advanced TAGL Query

#### Analytical Units

- 08 — Input + Control: Search for Records

#### User Story

As a user,  
I want to enter a TAGL query directly,  
so that I can compose advanced queries beyond the facet controls.

#### Acceptance Criteria

##### Scenario: Submit a valid direct TAGL query

**Given** that I use the advanced query option  
**When** I enter valid TAGL directly and submit  
**Then** the query runs as entered.

##### Scenario: Invalid direct TAGL is reported, not bypassed

**Given** that I use the advanced query option  
**When** I submit TAGL that fails to parse or validate  
**Then** the same TAGL parsing and validation apply as to any query  
**And** the returned TAGL errors are reported rather than bypassed.

### US-017 Suggest Recent and Frequent Records

#### Analytical Units

- 09 — Input + Control: Retrieve Familiar Records

#### User Story

As a user,  
I want recent and frequently used records suggested when I focus an empty search
field,  
so that I can return to familiar records without searching.

#### Acceptance Criteria

##### Scenario: Show recent and frequent records on empty focus

**Given** that the search field is empty  
**When** it receives focus  
**Then** a clearly labeled "Recent and frequent records" list is shown.

##### Scenario: Typing replaces the list

**Given** that the recent-and-frequent list is shown  
**When** I begin typing  
**Then** that list is removed  
**And** query-based suggestions may replace it without executing the full search.

##### Scenario: Suggestions do not bypass explicit search

**Given** that suggestions are shown  
**When** I want full results  
**Then** I must still submit the search explicitly.

##### Scenario: Personal history is private to me

**Given** that suggestions draw on my personal access history  
**When** another user searches  
**Then** my personal history does not alter their results.

### US-036 Search by Voice

#### Analytical Units

- 03a — Input + Control: Dictate and Command by Voice

#### User Story

As a user,  
I want to enter search terms by voice,  
so that I can search without typing.

#### Acceptance Criteria

##### Scenario: Dictate search terms

**Given** that a microphone is available  
**And** I start voice dictation in the search field  
**When** I speak search terms  
**Then** the transcribed terms populate the query.

##### Scenario: Search runs on explicit submission

**Given** that I have dictated search terms  
**When** I have not submitted  
**Then** the search does not run  
**And** it runs only when I submit explicitly.

##### Scenario: Voice search does not create or change records

**Given** that I search by voice  
**When** the results are presented  
**Then** no records are created or changed.

##### Scenario: Fall back to the keyboard

**Given** that no microphone is present or permission is denied  
**When** I search  
**Then** the keyboard remains fully available.

### US-038 Capture Photos and Video with Voice Notes

#### Analytical Units

- 06b — Input + Control: Capture Photos and Video with Voice Notes

#### User Story

As a user,  
I want to capture photos and video with the device camera, optionally with a
dictated voice note,  
so that I can add records directly from what I observe.

#### Acceptance Criteria

##### Scenario: Capture a photo or video as a record

**Given** that a camera is available and permitted  
**When** I capture a photo or video  
**Then** the captured media is added as a file-backed record  
**And** its presentation specialization is determined as for any file-backed
record.

##### Scenario: Capture with a dictated voice note

**Given** that a microphone is available  
**When** I capture media and dictate a note with it  
**Then** the note is stored  
**And** the note is automatically associated with the captured media, with the
media as `_from` and the note as `_to`.

##### Scenario: Transcribe a captured recording

**Given** that I capture an audio or video recording  
**When** a transcript is produced  
**Then** the transcript is automatically associated with the recording, with the
recording as `_from` and the transcript as `_to`.

##### Scenario: Storage remains deliberate

**Given** that I have captured media  
**When** I have not submitted the Add Record form  
**Then** the captured media is not stored  
**And** storage occurs only on submission.

##### Scenario: Fall back to file selection

**Given** that no camera or microphone is present or permission is denied  
**When** I add a record  
**Then** file selection remains available.

## Low Priority — View + Control User Stories

### US-025 Review Application Events

#### Analytical Units

- 14b — View + Control: Review Application Events

#### User Story

As a user,  
I want to review operations, warnings, and failures, and open the records they
concern,  
so that I can understand what the application has done and investigate issues.

#### Acceptance Criteria

##### Scenario: Show user-relevant events newest first

**Given** that events have been logged  
**When** I open the event viewer  
**Then** completed operations, warnings, and failures relevant to me are shown
newest first.

##### Scenario: Filter and search events

**Given** that the event viewer is open  
**When** I filter by type or time, or search event content  
**Then** the presented events are narrowed accordingly.

##### Scenario: Expand an event for technical details

**Given** that an event is shown  
**When** I expand it  
**Then** its technical details are revealed.

##### Scenario: Open an affected record from an event

**Given** that an event references an affected record  
**When** I follow the link  
**Then** the record opens using the shared record-promotion behavior.

##### Scenario: Expose diagnostic events through an explicit filter

**Given** that more extensive diagnostic events exist  
**When** I apply the diagnostic filter, subject to permissions  
**Then** those diagnostic events are shown.

##### Scenario: Filtering does not change what is logged

**Given** that I filter the event viewer  
**When** the presented events change  
**Then** the underlying logging is not changed  
**And** retention is governed by system policy.

##### Scenario: Retrieve older events across sessions

**Given** that older events have been retained  
**When** I page back through history  
**Then** retained events are retrieved  
**And** history is preserved across sessions.

## Low Priority — Input + Control + View User Stories

### US-026 Customize Presentation Settings

#### Analytical Units

- 14c — Input + Control + View: Customize Presentation Settings

#### User Story

As a user,  
I want to choose presentation settings such as a Light or Dark theme,  
so that I can adjust the interface to my preference.

#### Acceptance Criteria

##### Scenario: Apply a sensible default before customization

**Given** that I have not set a preference  
**When** the application is presented  
**Then** it uses its sensible presentation default.

##### Scenario: Choose a supported theme

**Given** that I open presentation settings  
**When** I choose a supported theme, such as Light or Dark  
**Then** my chosen theme controls my presentation  
**And** the preference is persisted in my own tagspace.

##### Scenario: User settings do not override system configuration

**Given** that I change my presentation settings  
**When** they are applied  
**Then** system logging, storage destination, and retention configuration are
not changed.

## Low Priority — Control + View User Stories

### US-033 Reproduce a Selected Trail

#### Analytical Units

- 20 — Control + View: Share and Include Trails

#### User Story

As a user,  
I want to reproduce a selected trail and connect it into an existing local trail,  
so that I can incorporate someone else's trail into my own memex.

This story captures the **future** selective-reproduction capability described in
AU 20; it is recorded here for traceability and is not part of the initial
whole-tagspace share/include in US-032.

#### Acceptance Criteria

##### Scenario: Retrieve and execute a stored query at a chosen revision

**Given** that a stored query selects a trail's material for reproduction, while
the trail itself remains a `tagd:memex:trail`  
**When** I retrieve the stored query through HTTP GET and execute it against its
remote source tagspace  
**Then** it runs at the latest state or an explicitly selected revision  
**And** an unknown, unavailable, or unauthorized revision is a fatal execution
error without silent fallback.

##### Scenario: Store the reproduced trail material locally

**Given** that I reproduce a selected trail  
**When** the reproduction completes  
**Then** the reproduction is intended to store the trail's own material locally,
for example its definition, membership, trailhead, saved routes, member
associations and anchors, endpoint records, and required definitions  
**And** the exact dependency boundary that keeps a reproduction from collecting
unrelated material remains to be specified  
**And** external resources that are not bundled remain identifiable references.

##### Scenario: Selective reproduction avoids unrelated material

**Given** that I reproduce a selected trail  
**When** its scope is determined  
**Then** the reproduction is intended not to follow unrelated associations.

##### Scenario: Connect reproduced material to a local trail explicitly

**Given** that I have reproduced trail material  
**When** I connect it to an existing local trail  
**Then** the connection is made explicitly  
**And** the reproduction does not invent connections to local trails.

## Low Priority — Control User Stories

### US-037 Navigate by Voice

#### Analytical Units

- 03a — Input + Control: Dictate and Command by Voice

#### User Story

As a user,  
I want to issue navigation commands by voice,  
so that I can navigate without the keyboard or pointer.

#### Acceptance Criteria

##### Scenario: Issue a voice navigation command

**Given** that voice navigation is available  
**When** I issue a mapped voice command  
**Then** the system performs the same operation as the corresponding visible
control or keyboard shortcut.

##### Scenario: Voice navigation does not create records

**Given** that I navigate by voice  
**When** I issue a navigation command  
**Then** no record is created by the navigation.

##### Scenario: Voice is not the only means of navigation

**Given** that a navigation operation is essential  
**When** voice is unavailable  
**Then** visible controls and keyboard shortcuts remain available for it.

##### Scenario: Voice capture requires an explicit start and shows listening

**Given** that I use voice navigation  
**When** voice capture is active  
**Then** it required an explicit start  
**And** a listening indicator is visible.
