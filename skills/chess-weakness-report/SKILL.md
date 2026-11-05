---
name: chess-weakness-report
description: Find the one recurring chess weakness costing a player most against the rating band above them, with a measured target from their own games.
---

# Chess weakness report

Use this skill when the user gives a chess.com or Lichess username and asks what to improve, wants a measured target, or wants a free report.

## Call

```http
GET https://api.getonemove.app/v1/free-reports/chesscom/{username}
GET https://api.getonemove.app/v1/free-reports/lichess/{username}
```

Optional `time_class=rapid|blitz`. A `202` means queued: poll the returned `status_url` or `/v1/jobs/{job_id}`.

## Return

Summarise the Constraint name, the player's metric, the Target for the band above, the number of games, and the one short written paragraph. Do not invent a number.

Public endpoint. No key. Rate limited. Docs: https://getonemove.app/docs/api
