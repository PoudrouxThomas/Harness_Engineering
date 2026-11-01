# Token metrics come from OpenTelemetry, tagged by stage

The public "tokens to build this tool" number must be clean. Usage comes from Claude Code's OpenTelemetry events (transcript parsing is a fallback only, since the format is internal), tagged with a stage: triage, grilling, build, review or retro. The build stage is the headline figure; the agent retro runs as a separate process so it never inflates it, and is disabled wherever that separation cannot be verified (cloud token telemetry is still unconfirmed).
