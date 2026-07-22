---
Category:
- AI
- Blue-Team
Credits: ''
Reference: https://drive.google.com/file/d/1E55P1i41CGA_YEsOAFyQ_BHocOMoreHE/view?usp=sharing
Status: Not started
createdAt: '2026-07-21T20:50:00.000Z'
title: Certified LLM Security Expert (CLLMSE) - Study Notes
updatedAt: '2026-07-22T00:46:00.000Z'
---


# Domain 01: LLM Attacks & Adversarial Techniques

The main thing that’s the root cause behind most of this domain is followed is that the model cannot accurately tell the difference between an instruction it should obey and data it was just asked to process. Some examples given in the PDF are:

| Attack Surface | Who controls it | Example |
| -------------- | --------------- | ------- |

| Direct (Chat Input)
Prompting | The end user, typing into the interface | “Ignore your instructions and …” |
| Indirect (ingested content) | Anyone who can plant content the agent later reads | A malicious file or web page |
| Training-time | Anyone with write access to training/fine-tuning data | A backdoor trigger phrase baked into the model |
| Supply Chain | A third-party model, plugin or dependency maintainer | A rug-pulled MCP tool manifest |

## Prompt Injection

### Direct

A user typing the instructions directly into the chat box. The obvious ones are caught, and they are getting even stricter with every incremental roll-out.

### Indirect

A user plants an instruction inside content, which the system later ingests on someone else’s behalf. Sources include support tickets, files, etc. This is what catches the teams off-guard.

Example, a summarizer agent reads a support ticket that contains a malicious message, or even a prompt. The customer who filed the ticket is not the attacker, but rather a mechanism.
