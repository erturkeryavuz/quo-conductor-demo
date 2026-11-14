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

## Limits

- The model is small and local. It handles single-tool requests well and longer plans less reliably. Answers are shown exactly as produced, including one odd remark in the approved-write session.
- The recording waits briefly before answering an approval, as a person would. Journal entries are placed by the backend's own timestamps.
- QUO is a local, single-user runtime. Cloud deployment and multi-user operation are outside its scope.

## About this repository

It holds only the built, static demo, its screenshots and a 38-second walkthrough video (`media/quo-walkthrough.mp4`). QUO's source code is private.

Third-party licences: [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

© 2026 Ertürk Eryavuz
