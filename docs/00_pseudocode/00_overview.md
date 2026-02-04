# Pseudocode: Base API Client (Communication Layer)

_**Purpose**_

- Handle all generic HTTP communication
- Be completely unaware of any specific API domain

_**Responsibilities**_

- Store base configuration (base URL, headers, auth info)
- Build full request URLs from parts
- Send HTTP requests
- Handle errors consistently
- Parse responses into usable data

_**Does NOT**_

- Know endpoints
- Know required parameters
- Know workflows
- Know what the data means

_**Expected interaction**_

- Subclasses provide:
  - base URL
  - authentication details (if any)
- Subclasses use communication methods
- Subclasses do not override communication behavior unless necessary

## Pseudocode: Concrete Client (Example: Weather)

_**Purpose**_

Represent one specific API and its rules

_**Responsibilities**_

- Know required inputs (city name vs coordinates)
- Encode multi-step workflows (e.g., geocode → weather)
- Expose meaningful domain actions (e.g., “get weather for city”)

_**Does NOT**_

- Reimplement HTTP logic
- Handle low-level errors directly
- Expose raw endpoints to callers

_**Expected interaction**_

- Caller asks a domain question
- Client performs required steps internally
- Client returns a clean result
