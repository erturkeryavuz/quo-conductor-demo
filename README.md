# QUO · Conductor

**[Open the demo](https://erturkeryavuz.github.io/quo-conductor-demo/)**

Recorded sessions of QUO, a local AI orchestration runtime, replayed from its own journal: what it planned, what it ran, what it asked a person to approve, and when the model was working.

This is a recording. No model runs in your browser, there is no prompt box, and the page makes no network connections.

![A file write waiting for a person's approval](media/quo-03-waiting-for-approval.png)

## What QUO is

QUO turns a request into a plan, runs each step through a declared capability, and writes every event to a durable journal. A step that would change the workspace stops and waits for a person, who approves or rejects exactly the action shown. Runs can be cancelled, and every outcome is recorded.

## What the demo shows

Seven sessions recorded from the real backend over its WebSocket protocol, with a small local model (`llama3.2:3b`) on a demo workspace:

- A calculation, a file read, a knowledge-base search and a host-load reading.
- A file write that waits for a person and is **approved**, then applied.
- A file write that is **rejected**: the step fails and nothing is written.
- A run **cancelled** by the user partway through its plan.

Each session plays at its recorded timing. The screen at any moment is rebuilt by passing the recorded journal entries through the same state reducers that QUO's own interface uses, so what you see is derived from the record rather than drawn separately.

The central view lays a session on one time axis: the run's phases, when the model was in use and for how long, each step, time spent waiting for a person, and tokens as they streamed. Beside it are the conversation, the plan, and the journal, where any entry opens to its recorded payload.

![An approved write, applied and verified](media/quo-02-approved-write.png)

## Private Product Preview

The demo above is a replay of recorded sessions. QUO itself is a private application that runs on my own machine against its local backend; it is not publicly accessible, and nothing on this site connects to it.

These screenshots are of that private application, taken during real runs against the backend with the same local model. The figure on the left is QUO's activity indicator: its colour follows the phase the backend records, the outer ring has one segment per step of the plan, and the open ring means it is waiting for a person.

**A finished run, conversation first.** The request, QUO's answer, and what the journal records about the run.

![QUO private app: a finished calculation run](media/private-quo-01-conversation.png)

**An approval request.** A file write stops before anything is changed; the person approves or rejects exactly the action shown, bound to its digest.

![QUO private app: a file write waiting for approval](media/private-quo-02-approval-request.png)

**After approval, with Run details open.** The recorded decision and effect, the plan, the time score and the journal.

![QUO private app: the approved write with the run details panel](media/private-quo-03-approved-with-run-details.png)

**On a phone.**

<img src="media/private-quo-04-phone.png" alt="QUO private app on a phone, waiting for approval" width="300">

## Limits

- The model is small and local. It handles single-tool requests well and longer plans less reliably. Answers are shown exactly as produced, including one odd remark in the approved-write session.
- The recording waits briefly before answering an approval, as a person would. Journal entries are placed by the backend's own timestamps.
- QUO is a local, single-user runtime. Cloud deployment and multi-user operation are outside its scope.

## About this repository

It holds only the built, static demo, its screenshots and a 38-second walkthrough video (`media/quo-walkthrough.mp4`). QUO's source code is private.

Third-party licences: [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

© 2026 Ertürk Eryavuz
