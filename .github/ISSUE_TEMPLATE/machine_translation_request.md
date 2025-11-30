---
name: Machine translation request
about: Request machine translation to a specific language afer forming a proofread team
title: 'MT Request:'
labels: 'machine_translation'
assignees: ''

---

**Language Code** (to be filled in by the requester)
One language code to run a machine translation such as "ja-JP"

**Proofread Team** (to be filled in by the requester)
Team Lead: (full name,slack ID on owasp.slack.com, gitthub ID(, linkedin or github ID (optional)
          e.g., John Doe, @johndoe, @JohnDoe_Github
Team Members:  (full name,slack ID on owasp.slack.com(, github ID (optional)) (, linkedin or github ID (optional)

Notes:
- Team Lead github ID is required.
- 2, 3, or 4 more additional members required for neutrality.
- When the English original is ready for localization, the project owner will submit a 'Document Build Request' with 'mt' option, then merge the MT'ed markdown and custom JSON files to the language directory such as 1.0/blddoc/ja-JP on the main branch from which the team can start proofreading.

Next Steps:
- When proofread is done, the team lead can submit a pull request of the markdown and custom JSON files to the language directory.
- When accepted, the PR'ed markdown and custom JSON files are merged to the main branch.
- When the project is ready for publish it, the W.I.P. watermark will be removed and the publish-read PDF will be merged to main.
