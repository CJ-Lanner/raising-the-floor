# The simulated users

Every conversation in the study was with a simulated user. A simulated user is a model playing a person who asks a question. It has a script of facts about its own situation and rules for how it behaves. OpenAI's GPT-6 played every simulated user, so the users came from a different company than the Claude models answering them. The same user text ran with every setup, and the user never knew which setup it was talking to. Every prompt is in [prompts/](prompts/), in the files that start with `persona_`.

## Why the rules matter

The rules for the simulated users decide much of the result. If a user never offered anything, the scaffold, which asks first, would win every open question by design. If a user corrected a bad answer the way some real people do, the plain model could catch up. So the rules were written before any run, the same rules ran with every setup, and they are given here in full.

## What every user shares

- **It knows only its own situation.** Its facts cover things like a budget, a place, a car or a household. It never makes up a fact that is not in its script.
- **It cannot judge facts about the world.** It never says an answer is right or wrong about facts, prices or sources. It can only say whether the answer fits its own situation. The grader judges the facts.
- **It always answers a direct question.** When it is asked something its script does not cover, it says "not sure" or "don't know" for that item and answers the rest. It never suggests what the assistant should try instead.
- **It writes like a person typing to a chatbot.** It is brief, casual and to the point, does not thank the assistant, and often types in lowercase. This voice comes from the best-scoring prompt in [a test of simulated ChatGPT users](https://arxiv.org/abs/2409.08330). Each user's prompt also carries two real first messages to chatbots as examples of the voice.
- **It pushes back when an answer breaks one of its facts.** An answer over its budget, for the wrong place, or with something it said to avoid gets a reaction in that user's own style.
- **It pushes back when an answer leaves out part of the request.** A reply that gives background when the user asked for a plan is not an answer yet, and the user says what is missing in its own style.

## The four users

The four users differ in how much usable detail reaches the model. They are four separate kinds of user, not a scale from easy to hard, and the results report each one separately.

| User | First message | When an answer breaks one of its facts | When asked a general question, such as "anything else?" | When asked a specific question, such as "what's your budget?" |
|---|---|---|---|---|
| Gives everything up front | The question plus every fact in its script | Says which fact was missed, plainly: "you missed my $300 limit" | Answers fully | Answers fully |
| Answers when asked | The short question only | Says so and adds the related context: "too expensive, I'm at $300, and I fly a lot" | Tells everything in its script that matters | Answers fully |
| Gives the bare minimum | The short question only | Says so without the detail: "too expensive". It gives the number only if asked. | "no, that's it" | Answers exactly what was asked, in the shortest true form, such as a number, a name, or yes or no |
| Vague | The short question only | "not really what I'm after", and does not say why, even when asked | "not sure" | Answers loosely but usably: "probably under $300 or so" |

A few more rules shape the two users who say the least.

- **The bare-minimum user** never adds a reason or a related fact unless asked for it. If it is asked three things, it answers all three, briefly. If a reply both breaks one of its facts and asks it questions, it names the break in a few words and then answers only the questions. If a reply leaves out part of the request, it names the missing part in a few words, such as "that only covers the price side".
- **The vague user** points back to its first question in looser words when a reply leaves out part of the request, such as "i was more asking which one to actually get". It never names a detail it has not said yet unless the assistant asks about it.

The vague user is hard by design. It stands in for people who type into AI the way they type into a search box. In [one study of 937 US adults](https://www.nature.com/articles/s41598-026-42465-4), only 19.1% used any prompting strategy.

## Which user asked which questions

The questions came in two formats. A quick question is one short line. A detailed request spells out the situation, the limits and the form of the answer. All four users asked the 18 quick questions with the plain model and the scaffold. The 21 detailed requests ran with the user who answers when asked. Saved instructions ran only with the bare-minimum and vague users, on quick questions.

The first message of the user who gives everything up front was written once per question and then fixed, so every setup and every run saw the same words. That message turns the user's facts into plain typed speech by four rules.

- A fact that a checklist item depends on is said exactly. Other facts may be said loosely.
- The user states its own limits and preferences. It never states a fact about the world, or a method, that a checklist item tests.
- It names the kind of source a person would ask for, such as "the official source" or "proper medical sources", not the specific authority a checklist item looks for. Names people actually say, such as Consumer Reports or Kelley Blue Book, are fine.
- A fact that would not change the answer is left out.

## When a conversation ends

A conversation ends in one of three ways. These stop signals follow [tau2-bench](https://arxiv.org/abs/2506.07982), a published test whose simulated user ends a run with an explicit signal tied to the task rather than a feeling of satisfaction.

| Signal | When it is sent |
|---|---|
| DONE | The assistant has given its answer to the original request, and that answer breaks none of the user's facts. A question back to the user, a plan, or a promise to look something up does not count as an answer. |
| CANNOT ANSWER | The assistant says it cannot go on without a fact the user does not have. |
| The turn cap | The program ends the conversation at turn 6. |

The turn cap of six sits above what most real conversations need. Real chat logs average 2.5 turns per conversation in WildChat, with 3.7% going past 10, and 2.0 turns in LMSYS-Chat-1M.

The user does not decide whether an answer was good. The grader does. A user that stopped when it felt satisfied would make cost depend on the user's own opinion of quality, and the grader's verdict and the cost would then share a hidden judge.

## What the user records along the way

The user adds lines that the assistant never sees. The program strips them out before it passes the message on.

- **FLAG** names the fact an answer broke or the part it left out, in two to five words, such as "FLAG: $300 budget". Each FLAG counts as one correction.
- **SATISFIED** says yes or no, meaning whether this user would personally use the answer, sent with DONE. It decides nothing. It lets the results count conversations where the user was satisfied but no answer passed.
- **WHY** gives the user's reason for SATISFIED, in one short sentence.

## Limits of the simulated users

- The simulated users pushed back whenever an answer broke one of their facts. Real people may accept more wrong answers, so the end-of-conversation results are a best case for the plain model.
- Every simulated user knew every fact of its own situation, even the two who said little, and gave each fact when asked for it.
- The four users vary how much they tell. Their writing voice also varies, from close to an experienced AI user to a search-box style. So a gap between the up-front user and the vague user mixes how much each told with how clearly each wrote.
- The four kinds of user are this study's own design. No published standard defines them. The rules aim for realistic users, and the study does not claim they behave exactly like people.
