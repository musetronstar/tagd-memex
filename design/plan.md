> When user stories are complete, I plan to hand over `analytic-units.md` and `user-stories.md` to Claude Design to create UI mockups before we create the detailed software specifications. Then Codex will help me write the front-end code as a single page HTML app (plus HTML partials perhaps ctemplate compatible mustache templates)  from the UI mockups, along with mocked JavaScript unit tests knowing that the tagd app and httagd service will be addressed after that. Is that a sound plan? Or, should we write the software specification first, before working on the front-end?

---

Your plan is sound with one important refinement: write a **lightweight UI contract before the mockups**, then write the detailed software specifications after the mockups and interactive prototype have validated the design.

Writing the complete software specification first would force us to decide routes, template contexts, service boundaries, and data structures before seeing how the interface actually works. The mockups will expose missing states and awkward interactions that the AUs and user stories cannot reveal by themselves.

At the same time, sending only the AUs and user stories to Claude Design leaves too much room for it to invent interaction behavior. Give it a concise UI design brief derived from the approved stories.

I recommend this sequence:

1. **Complete the analytical units.**
   Done.

2. **Complete the user stories and acceptance criteria.**
   These establish what the user must be able to accomplish and what observable
   behavior counts as success.

3. **Create a lightweight UI design brief.**
   This should define:

   * application terminology;
   * information architecture;
   * the Desk regions;
   * wide and narrow viewport behavior;
   * active, primary, secondary, expanded, collapsed, loaded, and empty states;
   * Source and Target presentation;
   * RecordStack behavior;
   * record, association, and trail navigation;
   * stable URL and browser-history expectations;
   * required controls and their placement;
   * record-type renderers;
   * loading, empty, success, validation, and error states;
   * accessibility requirements; and
   * the exact user stories each mockup must demonstrate.

   This is an interaction contract, not the software specification.

4. **Have Claude Design create the mockups.**
   Request all material states rather than only polished “happy path” screens.
   For example:

   * empty and loaded Desk;
   * wide and narrow layouts;
   * content record and association record;
   * Source active and Target active;
   * collapsed counterpart;
   * search with no results, exact result, and several results;
   * Add Record and Add Association workflows;
   * trail junctions and trail switching;
   * loading and error presentation; and
   * keyboard focus and active-state cues.

5. **Review the mockups against the user stories.**
   Each acceptance scenario should be demonstrable in the mockups. Any design
   decision discovered here should update the AUs or user stories before code is
   written.

6. **Build an interactive front-end prototype with mocked services.**
   A single entry page with HTML partials is appropriate. I would treat it as a
   **standalone interactive prototype**, without committing yet to a
   client-heavy SPA architecture.

   Structure it for progressive enhancement:

   * semantic HTML provides the document structure;
   * templates render records and application states;
   * CSS handles responsive presentation;
   * JavaScript adds interaction and history behavior; and
   * a mock service adapter supplies fixtures and simulated responses.

   This will make it easier to replace the mock adapter with httagd later.

7. **Test the prototype against the approved stories.**
   Unit tests are useful for rendering, state transitions, URL generation, and
   the mock service boundary. Browser-level interaction tests should also cover
   complete acceptance scenarios such as promotion, Browser Back, responsive
   view changes, and association direction.

8. **Write the detailed software specifications.**
   By this point, the specification can describe behavior that has been seen
   and tested rather than imagined. It should define:

   * httagd routes and HTTP methods;
   * tagdurl-to-TAGL mappings;
   * request and response representations;
   * template names and template context fields;
   * HTML-partial boundaries;
   * record, association, trail, and search result schemas;
   * validation and permissions;
   * error and event responses;
   * Filepile interactions;
   * persistence and transaction limitations;
   * browser-history and URL-state encoding;
   * accessibility requirements; and
   * the boundary between server rendering and JavaScript enhancement.

9. **Integrate the prototype with httagd and tagd.**

One architectural caution: Google ctemplate syntax and Mustache syntax resemble
each other, but they are not automatically interchangeable. Before writing many
partials, we should define the exact common subset we intend to use. Keeping
templates declarative and free of business logic will make later conversion or
server rendering much easier.

The mock layer should also expose a small interface rather than being called
directly throughout the UI. Conceptually:

```javascript
memex.search(query)
memex.loadRecord(id)
memex.addRecord(input)
memex.loadAssociations(id)
memex.addAssociation(input)
memex.loadTrail(id)
memex.extendTrail(input)
```

The exact interface will come from the completed user stories. The front end
can initially implement it with fixtures; httagd can later implement the same
boundary through tagdurls and TAGL.

So I would not write the full software specification before UI work. I would
write a small UI contract, produce and review the mockups, build a tested
interactive prototype, and then use what we learned to write the detailed
specifications before production integration.

