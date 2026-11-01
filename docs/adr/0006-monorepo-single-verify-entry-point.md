# Monorepo with a single `npm run verify` as the definition of done

Angular app, .NET API, harness scripts and agent config live in one repo so a single command can check everything. Agents, the Stop hook (fast tier) and CI (full tier) all call `npm run verify`, so they cannot disagree about what passing means.
