# A Practical Playbook for Building with AI Tools

AI tools are most useful when the human keeps ownership of the problem, the boundaries, and the acceptance decision. This playbook turns that idea into a repeatable workflow you can use with a coding agent, a research assistant, or a team of tools.

## 1. Start with the operator's problem

Describe who needs the tool, what they are trying to do, and what makes the current process hard. State the outcome in observable terms. Keep proposed features out of the problem statement until you know they are needed.

Ask:

- Who is the user, and what task are they trying to complete?
- What should become easier, safer, or more reliable?
- What evidence would show that the result works?

## 2. Set boundaries before work begins

Write down the non-negotiables: data location, network access, permissions, supported platforms, reversibility, and what must not change. Decide which actions need approval and which sources are authoritative.

Examples from these projects:

- **XtracsysCode** keeps built-in model requests on a configured loopback server. File writes and shell commands are approval-gated, while the documentation clearly says approved shell and plugin processes are not sandboxed.
- **LeetOffice** gives an agent an explicit identity and only the tool grants selected for it. Its writes remain attributable in the Git audit trail.
- **XtracAppAudit** inspects app bundles without launching them. Online checks and Bonjour device discovery are separate user controls; Bonjour sees devices advertising supported services, not every device on the network.
- **MacSpaces** moves deletions to Trash by default. Ollama orphan cleanup checks a fresh audit again before removal.
- **Xtracsys Editor** preserves encoding, line endings, and final-newline state, and asks before overwriting a file changed elsewhere.

These are project-specific boundaries, not a promise that every product behaves the same way.

## 3. Turn the outcome into a small plan

Break the work into changes that can be reviewed independently. For each change, name the files or component boundary, the expected behavior, and a check that could prove it. Keep non-goals in the brief so an agent does not expand scope to fill silence.

A useful task is small enough that a reviewer can answer: “Did this change satisfy the requirement, and what evidence supports that?”

## 4. Delegate execution, retain product decisions

Give tools bounded work with the needed context, not ownership of the whole product. Ask them to inspect relevant code and docs, explain assumptions, and report limitations. Keep decisions about user impact, data handling, permissions, and release readiness with the human owner.

When several tools are involved, assign clear interfaces and have one owner reconcile conflicting recommendations. A confident answer is not evidence; ask for the file, behavior, or run result that supports it.

## 5. Review the result against the brief

Read the actual change. Check whether it:

- Meets each acceptance criterion.
- Preserves unrelated behavior and established project patterns.
- Respects the data, network, and permission boundaries.
- Handles failure and uncertainty honestly.
- Updates user-facing documentation where behavior changed.

Ask a reviewer to look for specific risks and missed cases. Keep review notes private unless they become a useful product decision, security advisory, or contributor-facing explanation.

## 6. Verify, then make a clean handoff

Run the checks relevant to the change and record what actually ran. Separate automated results from manual checks. State known limits instead of turning a partial check into a broad guarantee. The owner decides whether the evidence is good enough to publish.

A clean handoff gives the next person:

- The purpose of the change.
- How to build, use, or review it.
- The verification performed and the state it covered.
- Known limits and where to report issues.

## Copyable templates

### Project brief

```text
Project:
Primary user:
Problem to solve:
Desired outcome:
Non-negotiable constraints (data, network, permissions, platforms):
Out of scope:
Acceptance criteria:
Release decision owner:
```

### Scoped task

```text
Outcome:
In scope:
Out of scope:
Relevant files or interfaces:
Constraints to preserve:
Acceptance checks:
Required documentation:
Report assumptions and known limits:
```

### Review request

```text
Intent:
Files or behavior changed:
Acceptance criteria:
Evidence already gathered:
Known limitations:
Please focus on:
```

### Release handoff

```text
Project and version:
Source commit:
What changed:
Build and verification performed (include exact result):
Manual checks performed:
Known limits:
Install or update instructions:
Support and security contact:
```

## Using the examples

The five Xtracsys projects show different ways to make priorities concrete: local model boundaries and approval-gated tools, attributable agent access, read-only audit evidence, recoverable cleanup, and byte-faithful file saves. Borrow the decision process and adapt the controls to your own product; do not copy a control without understanding the risk it addresses.
