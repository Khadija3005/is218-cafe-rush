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
