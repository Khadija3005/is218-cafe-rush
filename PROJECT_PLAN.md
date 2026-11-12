# Café Rush - Creative Project Plan

**Course:** IS218-003 | **Stage:** Review 1 - Plan | **Date:** November 12, 2026

## Two concepts and choice

| Concept | Useful interaction | Saved record | Scope |
| --- | --- | --- | --- |
| Café Rush - selected | Make customer drinks | Verified round score and order outcomes | Three recipes, five orders, single player |
| Study Session Tracker | Enter study subject and minutes | Personal study history | Manual logging and totals |

Café Rush was selected because making drinks and completing orders is a more playful project. This is a preference and scope decision, not evidence that other players prefer it.

## Audience and complete promise

Audience: college students wanting a quick casual game. Register and log in, play a five-order café round, save the server-verified result, view a private score history and best score, update display name/password, and log out.

Baseline rules: three fixed recipes (espresso, latte, mocha); the server assigns five orders. Select ingredients and submit each drink once. A correct recipe earns 20 points; an incorrect recipe earns zero and advances to the next order. Maximum score: 100. No multiplayer, chat, payments or café-building system. Timing is an optional experiment, not required for the baseline.

## Stack

Python, Flask, Jinja/HTML/CSS, small JavaScript interactions, SQLite and pytest. The GitHub Pages research site is documentation; the future Flask game needs separate server hosting. Dependencies and runtime compatibility are untested.

## Five stories and planned checks

1. As a player, I want to register, log in and log out to keep my results private. Check duplicate usernames, incorrect credentials and signed-out access.
2. As a player, I want to select ingredients to complete customer orders. Check all three recipes and incorrect combinations against server-side rules.
3. As a player, I want finished rounds saved so I can return later. Check persistence after logout/login and restart; repeated final submissions must not create duplicate results.
4. As a player, I want private history and a best score to see progress. Use two accounts to check isolation and accurate totals; reject another user's round IDs.
5. As a player, I want to update my display name and password to maintain my account. Require authentication and current-password confirmation for password changes; verify old/new credentials.

## Planned architecture

| Layer | Responsibility |
| --- | --- |
| Browser | Show order, ingredient choices and result |
| Flask routes | Accounts, round actions, dashboard and settings |
| Game service | Assign orders, validate recipes, advance state, calculate score |
| Repository | Parameterized SQL and transactions |
| SQLite | Users, rounds, order attempts and final results |

Requests pass through these layers; responses return as rendered HTML. The server owns the order sequence, progress and score rather than accepting a browser score. Derive ownership from the signed-in account, prevent replayed submissions, hash passwords, validate input and protect state-changing forms against CSRF. These are planned requirements, not implemented protections.

## Uncertain creative experiment - planned

Does a visible countdown make the game exciting or confusing? Compare five-order prototype rounds with and without a 90-second limit. Ask a classmate to identify orders, assemble drinks and describe pressure/confusion. Record errors, completion and comments. Keep the timer if it adds enjoyment without preventing understanding; otherwise defer it. If adopted, enforce timing on the server. No experiment results exist yet.

## Pattern experiment - planned

Compare recipe-validation conditionals with a recipe lookup/strategy interface using identical correct/incorrect recipe tests. Assess clarity and ease of adding a fourth recipe. No comparison has been run.

## Research and review

[Research site](https://khadija3005.github.io/is218-study-tracker/) | [Review issue](https://github.com/Khadija3005/is218-study-tracker/issues/1)

Peer review is pending and will be completed with a classmate in class. Ask the reviewer to open a source, explain the stack choice and identify an assumption/confusing part. Record specific feedback, decision/reason, change/check links and reviewer retry. Keep unfinished work open.

Career research site URL is needed for cross-links. The repository address is retained so existing submission links continue to work.

## Checks and AI assistance

The plan documents two concepts, audience, workflow, five stories, stack, architecture and planned experiments. Game implementation, tests and real peer review remain unrun. Official framework/database sources were reviewed during initial research. Game rules and enjoyment assumptions are design proposals. ChatGPT assisted with drafting and revising the plan.
