# Tasks

## 1. Shared Wake-Lock Lifecycle

- [x] 1.1 Integrate screen wake-lock acquisition and release with shared timer activity; verify wake locks are requested for active Stopwatch, Interval, and Tabata timing and startup countdowns, then released on stop, pause, reset, and completion.

## 2. Visibility and Failure Handling

- [x] 2.1 Handle browser release on page hiding and reacquire on visibility when timing remains active; verify hide/show recovery and that stopping or completing before an asynchronous request resolves leaves no wake lock held.
- [x] 2.2 Handle unsupported or rejected wake-lock requests without disrupting timer controls or timing; verify all timer modes continue normally when the API is absent or rejects a request.
