---
name: poker-leak-report
description: Analyse PokerStars cash-game hand histories and name the one poker leak costing a player most against the table format above them.
---

# Poker leak report

Use this skill when the user has PokerStars cash-game `.txt` hand histories and wants a measured leak report.

## Call

The upload is a browser multipart form at https://getonemove.app/poker: `screen_name` plus one or more `files`, at least 300 cash Hands. The API parses in memory, strips opponents' names, and deletes the files after building the report.

The resulting private report is readable at `GET https://api.getonemove.app/v1/poker-reports/{id}` when you hold the id. Do not share the id.

## Return

Name the poker Constraint, the player's metric, the Target for the table format above, the number of Hands, and the written paragraph. Cash games only.

Docs: https://getonemove.app/docs/api
