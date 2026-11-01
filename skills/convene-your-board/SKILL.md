---
name: convene-your-board
description: Put a question to one of the person's Idiosynt boards so several of their wits deliberate on it. Use when the person wants their board's view, wants several wits to weigh in on a decision, or replies to a sitting already under way, even without saying "chime in" (their reply goes to the board).
---

A board seats several of the person's wits. In a sitting, each wit speaks in turn, and Idiosynt adds a memo of where they agree and where they differ. The decision always stays with the person.

## Before the sitting

1. Call `list_boards` to find the board. If the person has more than one and has not said which, ask.
2. Confirm the question in the person's own words. Never write the question for them or widen it.
3. Seat the wits the person wants, up to five, using ids from `list_constructs`. If they have not said, ask whether to seat the whole board or particular wits.
4. Run one round unless the person asks for two, so they can respond sooner. Tell the person a sitting can take a minute or more.

## Running and presenting it

1. Call `board_deliberate` with the board's `room_id`, the question, the seated wits as `advisor_ids` and, if asked, `rounds`.
2. Present each wit's contribution in their own words under their attribution line, in the order returned. Then present the memo as returned. Do not summarize across wits, rank them, or say who is right.
3. Keep the `deliberation_id` from the result. While a sitting is under way, the person's next message about it is meant for the board, whether or not they say "chime in": call `board_chime_in` with their words, unchanged, as `message`. Do not answer it yourself, offer options or ask them to reframe it first. Each seated wit responds directly; present those responses the same way. Answer for yourself only when the person clearly addresses you rather than the board, or moves to another subject.
4. If Idiosynt returns a message saying the sitting is still under way or that something went wrong, show it as written and ask before trying again. Never start a second sitting on your own.
