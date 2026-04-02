# Routing Notes

## Choose Superpowers-first when
- the task needs local reasoning, fix options, tests, or debugging
- the bug is ambiguous and needs quick brainstorming
- the user cares most about implementation quality

## Choose GSD-first when
- the task is already scoped and only needs a narrow phase lock
- the work is being resumed after interruption
- the change must stay aligned with a shared project state

## Use both when
- you need a tiny scope lock, then a concrete fix plan
- you need a debugging pass, then a state update

## Never do
- full discovery plus full brainstorming in the same round
- duplicate design docs for the same fix
- broad refactors disguised as bugfixes
