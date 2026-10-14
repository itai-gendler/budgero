---
kind: configuration
of: capability-scenario
takesEffect: 'Fixed when the instance is built and deployed: the web app and the server are built for Budgero Cloud or for self-hosting.'
stability: An instance never changes edition while running; accounts of one edition do not carry over to the other.
alternatives:
- id: sign-in-with-budgero-account
  selectedWhen: The deployment is Budgero Cloud, the hosted service.
- id: sign-in-with-local-account
  selectedWhen: The deployment is a self-hosted instance.
---

# Edition

Budgero ships as the hosted Budgero Cloud and as a self-hosted edition built
from the same source; people sign in differently in each.
