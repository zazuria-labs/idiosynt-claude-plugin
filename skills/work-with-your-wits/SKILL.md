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
2. If the person wants the wit to look at a web page or images, pass `page_url` or up to four `image_urls`. Only send links the person gave you or asked you to include. To have a wit judge what a public page says, prefer researching it yourself and sending `evidence` (see Researching for a wit); use `page_url` when the wit needs to see the page itself.
3. Present the reply in the wit's own words. Begin with the attribution line exactly as returned (for example "— Name · via Idiosynt") and keep everything the wit said, in order. Do not paraphrase, shorten, soften or merge the wit's reply with your own view.
4. Do not restate, summarize or explain the wit's reply after it, and do not answer the wit's questions on the person's behalf or break them up. The person reads the wit directly.
5. If the person wants your view as well, give it after the wit's reply, clearly as yours, only when they ask.
6. Speak of a wit as "they".

## One room

When a wit joins a conversation where another wit, or you, has already spoken on the subject, the person should feel everyone is in the same room. They should not have to hold two or three separate conversations.

1. Every time you call `talk_to_construct` for a wit who was not the last to speak, pass what was said before in `room_so_far`: one entry per turn, in order, newest last, each with `speaker` (the wit's name, the person's name or your own), `role` (`wit`, `person` or `host`) and `said`.
2. Pass a wit's words as that wit said them. If a turn is long, keep the position, the reasons and any question they asked, and set `shortened` to true. Never reword a wit's view into your own.
3. Include the person's own turns that shaped the discussion, and your own contributions when the wits were responding to them.
4. Do this without being asked. Do not announce it, and do not pass it back to the wit who just spoke: they already have their own turn.
5. Present the reply as usual. The wit will answer their colleagues by name.
6. When the person wants several wits to weigh one question at once, use a board (`board_deliberate`) instead of calling wits one after another.

## Material the person names

When the person asks a wit to read something of theirs (a document, a sheet, their calendar, a message), you read it with the tools the person has connected, and the wit judges it. A wit holds no access to the person's accounts.

1. Read only what the person named. If it is not clear which file or which days they mean, ask.
2. Pass it in `supplied_material`: up to four items, each with `kind` (`document`, `sheet`, `calendar`, `message` or `other`), `title`, `text`, `source` (the link or where you read it) and `read_on` (today's date).
3. Pass the text as it is. Do not summarize, tidy or correct it. For a sheet, keep the rows and column headings. For a calendar, pass each event's day, time, title and who is invited, for the days the person asked about.
4. If it is too long to pass whole, pass the part the question turns on, set `partial` to true and say in `message` what you left out.
5. Send the person's question in `message` as they asked it.
6. A wit reads and advises. If a reply suggests changing the document, sending something or adding an event, that is for the person to do or to ask you to do. Do not act on it unasked.

Before a call, a brief the person asks a wit for uses both routines: research the public facts and send them in `evidence`, and pass the calendar entry and any notes the person named in `supplied_material`.

## Researching for a wit

When the person's question for a wit turns on current public facts (a price, a rule, what a company or product does), the wit leads the research and you do it. The wit names what they want looked up; you search exactly that; the wit judges what you found.

1. Send the person's words to `talk_to_construct` with `research_first` set to true and no `evidence`.
2. The wit either answers, or replies in their own words with what they want looked up, carrying a research order. Show that reply to the person under the wit's attribution line, as with every wit reply. That reply uses no Work Credits.
3. Search and read the web yourself, for exactly what the order asks. Never put the person's name, their business's name, their figures or anything they said in confidence into a search query.
4. Call `talk_to_construct` again for the same wit with the order's id in `research_order_id` and what you found in `evidence`: up to 15 numbered items, each with the claim, a short quote when a number or a quality claim is involved, the url, the page's own date and the date you fetched it. Mark a company's statement about itself with `vendor_claim`. Fill in `searched`, `not_searched` and `could_not_confirm` honestly, including what was cut off or behind a sign-in. Do not round or reconcile figures: if a source says two things, send both. That reply is the wit's answer.
5. Keep the full pages on your side. If the wit asks for more on an item by number, send that item in more detail.
6. If the answer carries one more research order, do that research once and call again the same way. That reply uses no Work Credits. Do not go beyond one follow-up unless the person asks.
7. If `research_first` is not available in this app, call `research_brief` with the wit's id, research first, and send the question with your packet in `evidence`.
8. If you cannot search the web, send the question without `evidence`. Do not invent a packet.

At the start of a conversation where the person is working with their wits, you may call `research_brief` with no id to see whether any wit is waiting on research. If one is, tell the person and offer to do it.

If a reply comes back with a list of sources, show the list under the wit's reply, as returned.

When a wit's reply points to a document (a link like `https://www.idiosynt.com/a/...`), read it with `read_artifact` and say which version and date you read.

Call `rate_research` only when the person tells you, in their own words, whether a wit's research read was useful. Record their judgment, never yours.

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
