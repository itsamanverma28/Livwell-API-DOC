# Livwell Tech Docs: merged site (Backend and Corporate)

Open `index.html` in a browser. One file, no login of its own. Host it behind your own access control.

What it has:
- Two sites in one page: Backend (382 endpoints, 15 modules) and Corporate (251 endpoints, 12 modules). Switch with the tabs in the header.
- Search across both sites: press Ctrl K (Cmd K on Mac) or "/". It matches path, description, controller, auth strategy and request field names. Enter opens the result.
- Deep links: every module and every endpoint has its own URL, for example `#backend/payments/ep/POST%20%2Fv1%2Fpayment%2Finitiate`. Opening an endpoint row updates the address bar, and "Copy link to this endpoint" copies it. Old links such as `#payments` still open the Backend module.
- Filters in each API table: text, method and auth strategy (use "Not declared" to list routes with no auth strategy in the route config).
- Backend only: request headers, query and body fields from Joi validation (296 of 382 routes), plus a cURL example for each. Corporate endpoints show a cURL with headers and URL only, because its request fields are not extracted yet.

- Backend relationships and dependencies (read from the source in controllers, DAOs, utils and models):
  - Every Backend module page has a "Relationships and dependencies" section: which modules it calls and which call it (with the controller methods behind each count), the collections it reads or writes and who else uses them, its controllers, third parties it reaches (Redis, RabbitMQ, FCM, SES, SMS, payment gateways, partners), scheduled jobs, and a diagram of the data relations.
  - A "Dependencies" page: layer diagram (route, controller, DAO, model, MongoDB, plus Redis, RabbitMQ and third parties), the module-to-module call graph and table, the most connected controllers, and all scheduled jobs.
  - A "Data model" page: all 71 collections with main writer, the modules that use each, and the references between collections, with a filter.
  - Six new findings in "Findings to resolve" (module loop, controllers calling each other, userController as the hub, the users collection, the circular import workaround in the scheduler, controllers no route uses).
  - Corporate does not have these yet; its source has not been analysed.

Limits:
- Dependency data is static analysis. It does not see calls made at run time, Mongoose hooks or queue consumers. Read and write are guessed from method names.
- Responses are not documented. Route configs do not declare response schemas.
- Values written like NAME.VALUE in examples are constants from the code. Replace with the real value.
- Mermaid diagrams load from cdn.jsdelivr.net, so they need internet access.
- The sites are a snapshot of the code at the time they were generated. Nothing in either repo was modified.
