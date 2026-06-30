# Loop Engineering Checklist

Use when improving the daily automation loop itself.

- [ ] The loop has a clear trigger and entrypoint.
- [ ] The loop state is explicit: `discover`, `plan`, `apply`, `evaluate`, `report`, or `blocked`.
- [ ] Inputs and required context are listed.
- [ ] Allowed and disallowed side effects are explicit.
- [ ] Reports are durable and easy to inspect later.
- [ ] Failures leave a useful handoff: state, last command, blocker, next action.
- [ ] The loop avoids repeated failing commands without changed hypotheses.
- [ ] The loop improves one small thing per run unless the user requested more.
