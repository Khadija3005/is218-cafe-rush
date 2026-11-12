# Study Session Tracker - Project Plan

**Course:** IS218-003  
**Stage:** Review 1 - Plan  
**Date:** November 12, 2026  
**Status:** Initial plan; application not implemented.

## Comparing two bounded concepts

| Area | Study Session Tracker | Rock-Paper-Scissors Game |
| --- | --- | --- |
| Audience | College students | Casual players |
| Useful interaction | Enter a study subject, duration and date | Play a round against the computer |
| Saved record | Subject, minutes and date owned by the user | Choices and outcome owned by the user |
| Private dashboard | Session history and total study time | Match history and win/loss/tie totals |
| Account access | Register, log in and log out | Register, log in and log out |
| Account maintenance | Update display name and password | Update display name and password |
| Scope boundary | Manual entry; no live timer, social features or calendar integration | Single player; no multiplayer or chat |
| Main uncertainty | Whether summaries help students understand study habits | Whether repeated rounds remain interesting |

## Selected concept and reason

The selected concept is the Study Session Tracker. It gives college students a practical way to record study sessions and review time spent across subjects. Its small workflow still requires account access, server-side security, persistent records, a private dashboard and account maintenance. Compared with the game, it connects more directly to a routine college task.

This is a design choice, not evidence that students prefer this concept. Usefulness and ease of use still need peer feedback.

## Audience and problem

The audience is college students studying for several courses who want a simple record of their study time. The assumed problem is that students may find it difficult to remember how much time they spent on each subject. This assumption has not yet been tested with users.

## Finished workflow promise

A student can create an account, log in, enter a subject, positive whole-number duration in minutes and session date, and save the session. After saving, the student sees it in a private dashboard with their history and total study time. Records remain available after logging out and back in. The student can update their display name and password, then log out.

The server must determine ownership from the authenticated account. Students must not be able to access another student's records by changing a URL or submitted identifier. Passwords must be stored as hashes and input must be validated on the server. These are planned requirements, not verified behavior.

## Proposed stack

| Part | Tool | Purpose |
| --- | --- | --- |
| Language | Python | Application and business logic |
| Server framework | Flask | Routes, requests and server-rendered pages |
| Interface | HTML, CSS and Jinja templates | Account forms, session entry and dashboard |
| Database | SQLite | Persistent user and study-session records |
| Testing | pytest | Validation, persistence, access and ownership checks |
| Version control | Git and GitHub | Project history and review records |

This stack is proposed and must be checked against the full course requirements before implementation. No dependencies have been installed and no runtime or compatibility checks have been run.

## Current scope and next work

Completed in this initial plan: two-concept comparison, audience selection, bounded workflow promise and proposed stack.

Still planned: five user stories, architecture sketch, uncertain creative experiment, research with verified original sources, published research site and career-site cross-links, real peer review recorded in issues, implementation and meaningful tests.

## Checks and AI assistance

- **Observed:** This plan compares two concepts and identifies the chosen audience, workflow and proposed stack.
- **Planned, not run:** Application tests, security checks, persistence checks and user feedback.
- **Planned, not completed:** Verification of stack choices against original documentation and full course instructions.

ChatGPT assisted with comparing concepts and drafting this initial plan. No peer feedback, user research or application test results are claimed.


## Review 1 update - stories, architecture and experiment

This update supersedes the earlier next-work list: the stories, sketch and experiment below are now documented. Application behavior remains planned and untested.

### Five user stories and planned acceptance checks

1. As a student, I want to register, log in and log out so my records stay private. Check: duplicate usernames and incorrect passwords fail; signed-out requests cannot access the dashboard.
2. As a student, I want to record a subject, minutes and date so I can track a study session. Check: empty subjects, invalid dates and zero/negative/non-integer minutes are rejected on the server.
3. As a student, I want sessions saved so I can return later. Check: a saved session survives logout/login and an application restart using the same database.
4. As a student, I want a private history and total study time so I can review progress. Check: two users see only their own records and correct totals; changing identifiers cannot expose another user's data.
5. As a student, I want to update my display name and password so I can maintain my account. Check: updates require authentication and current-password confirmation for a password change; the new password works and the old one fails.

### Architecture sketch (planned)

`
Browser: HTML/CSS and Jinja forms
  -> Flask routes: authentication, sessions, dashboard, account
  -> Services: input validation, ownership checks, totals
  -> Repository layer: parameterized SQL
  -> SQLite: users and study_sessions
`

Browser requests return through the same layers as rendered HTML. The server uses the authenticated user ID rather than trusting an owner ID from a form. CSRF protection is planned for state-changing forms. Passwords are hashed. Secrets and the live database stay out of Git.

Planned modules: app/__init__.py (factory), auth.py, sessions.py, account.py, services.py, repositories.py, templates/ and tests/.

Planned data: users(id, username UNIQUE, display_name, password_hash); study_sessions(id, user_id, subject, minutes, session_date). Each session belongs to a user.

### Uncertain creative experiment

Question: Does a weekly goal progress bar help students understand progress more quickly than a minutes-only summary?

Compare two paper/static mockups with the same example: 180 minutes studied toward a 300-minute goal. One shows numbers only; one adds a labeled 60% bar. Ask a classmate how many minutes remain and whether the goal is complete. Record answer accuracy, time and confusing wording. Try the views in alternating order if more than one peer participates. A single peer gives exploratory feedback, not proof of general effectiveness.

Decision rule: keep the bar if the reviewer correctly identifies 120 minutes remaining and understands the labels without extra explanation; otherwise revise or defer it. Both versions must keep readable numeric labels so color is not the only cue.

Status: PLANNED; no participant or result recorded.

### Pattern experiment (planned)

Compare direct SQL in a route with a small repository layer for saving/listing sessions. Use the same validation, persistence and ownership tests for both. Assess whether the repository makes those responsibilities easier to explain without unnecessary complexity. No comparison has been run.

### Research and peer review

Research site source: [docs/index.html](docs/index.html). Intended published address: https://Khadija3005.github.io/is218-study-tracker/ (publication must be verified).

Peer task: open an original source, explain the Flask/SQLite choice in your own words, and identify an assumption or confusing part. Record the actual feedback in a GitHub issue with the reviewer's name/handle, date, decision (implement/investigate/defer/decline), reason, change link, verification and reviewer retry. Keep unresolved work open with a next step. Peer review is pending; AI assistance does not replace it.

Career research site: URL not supplied yet. Cross-linking remains open; do not invent a career-site address.
