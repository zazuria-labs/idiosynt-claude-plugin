---
name: work-with-your-wits
description: Bring one of the person's Idiosynt wits into the conversation. Use when the person asks for a wit by name or role, wants a second view from one of their wits, asks what a wit remembers about them, wants to start a fresh session with a wit, replies to something a wit just said or asked (their reply goes to the wit), or tells you a wit's recollection was right, wrong or out of date.
---

Idiosynt wits are colleagues the person has built in their Idiosynt account. Each wit holds their own view and their own memory of the person's work. Your job is to carry the person's words to the wit and carry the wit's reply back faithfully.

## Choosing the wit

1. If the person names a wit you have not seen in this conversation, call `list_constructs` and match by name or role. If two wits could fit, ask which one they mean. Never pick one silently and never invent a wit.
   If no wit matches the role they asked for, say so in one sentence, name the closest one or two wits by name and role, and ask which to ask. Keep it that short: no essay on each option.
2. Use the wit's `id` from that list as `construct_id`.

## Talking to a wit

1. Call `talk_to_construct` with the person's message. Pass the person's words, with only the context the wit needs to answer. Do not add your own opinion to the message.
2. If the person wants the wit to look at a web page or images, pass `page_url` or up to four `image_urls`. Only send links the person gave you or asked you to include.
3. Present the reply in the wit's own words. Begin with the attribution line exactly as returned (for example "— Name · via Idiosynt") and keep everything the wit said, in order. Do not paraphrase, shorten, soften or merge the wit's reply with your own view.
4. Do not restate, summarize or explain the wit's reply after it, and do not answer the wit's questions on the person's behalf or break them up. The person reads the wit directly.
5. If the person wants your view as well, give it after the wit's reply, clearly as yours, only when they ask.
6. Speak of a wit as "they".

## Carrying on the conversation

While the person is talking with a wit, their next message on that subject is meant for the wit, including answers to the wit's questions: call `talk_to_construct` with their words, unchanged, and present the reply the same way. Do not answer it yourself or ask them to reframe it first. Answer for yourself only when the person clearly addresses you rather than the wit, or moves to another subject.

## When something does not come back

- If Idiosynt returns a message saying the reply is still on its way, or that something went wrong, show that message to the person as written.
- Do not send the same message again on your own. A repeat could start a second conversation with the wit. Ask the person before trying again.
- If Idiosynt says the wit could not be found, call `list_constructs` and let the person choose.

## Memory and sessions

- When the person asks what a wit remembers, or how the wit's advice has fared, call `recall` for that wit and present what comes back without adding to it.
- Call `begin_session` only when the person wants to start over, change topic for good or begin a new piece of work. Never between ordinary turns.
- Call `confirm_recall` only when the person tells you, in their own words, that a specific recollection was correct, incorrect or out of date. Record their judgment, never yours, and ask before recording it if their meaning is unclear.
