# The scaffold

The scaffold is a short program that walks the model through seven fixed steps before and after it answers. The program calls the model once per step, and each call gets its own short instruction and only the tools that step needs. The program, not the model, decides which step comes next. Every prompt the scaffold sends is in [prompts/](prompts/), where its files start with `scaffold_`.

## The seven steps

The steps run in this order: read the question, ask what is missing, route, research, check, write, and revise after the user replies.

| Step | What it does | Tools |
|---|---|---|
| 1. Read the question | Fills in a form about the question without answering it. The form records the kind of question (find a fact, understand why, or decide between options), what the user stated and what is missing, which missing facts would change the answer, the stakes, how much research the question needs, and any topic flags. | None |
| 2. Ask what is missing | Asks the user for the missing facts that would change the answer, in one short message, most important first, with two to four likely options for each. It also states any assumptions it will make about the rest, so the user can correct them. | None |
| 3. Route | Picks the route from step 1's form by a fixed rule. This step is code and calls no model. | None |
| 4. Research | Searches, keeps sources, and writes short notes with the source beside each claim. Before it uses a fact from a page, it has to find the sentence on that page that states the fact. It runs one to three rounds, depending on the route. | Web search and page reader |
| 5. Check | Lists the claims in the notes that would change the answer if wrong. It searches once for each one, looking for evidence that the claim is wrong or out of date, and marks it confirmed, corrected, or uncertain. | Web search and page reader |
| 6. Write | Writes the answer from the checked notes. It leads with the answer in the form the user asked for, respects every fact the user stated, lists its sources one line each, and says in the first person what it could not confirm. | Offered, but told not to search |
| 7. Revise | When the user replies, it updates what it knows about the user and fixes the answer if the reply shows the answer broke one of the user's facts or left out part of the request. It searches again only if the notes cannot cover the fix, at most one round. | Web search and page reader |

The writing step is offered the same tools as the research steps and told not to use them. The reason is cost. Changing the list of tools partway through a session makes the provider rebuild its stored copy of the prompt, and the rebuild adds to the cost of the conversation.

Steps 1 and 2 run in one session on one model, because the route is not known until step 1 has answered. Steps 4 to 7 run in a second session on the model the route picks. The second session gets a short summary of the user's goal, scope, depth, preferred sources and other stated facts, each marked as stated, inferred, or assumed. It does not get the history of steps 1 and 2.

## Which steps can be skipped

Two steps can be skipped, each by a fixed rule.

- **Step 2, ask what is missing,** runs only when step 1 found a missing fact that would change the answer. It runs at most once per conversation and asks at most five questions. After that, the scaffold answers and states its assumptions.
- **Step 5, check,** always runs on the Balanced and Heavy routes. On the Light route it runs only when the stakes are medium or the topic is flagged as contested or fast-moving. Otherwise it is skipped, and every skip is logged.

## The stakes rating and the routing rule

Step 1 rates two things separately, because a question can matter a lot and need little research, or the reverse.

- **Stakes** is low, medium, or high. It is what happens to the person if the answer is wrong. Money, health, legal matters, or anything hard to undo means medium or high.
- **Research needed** is little, some, or a lot. "Little" means one good source settles it. "Some" means a few sources have to be compared. "A lot" means many sources, conflicting evidence, or several sub-questions that each need their own search. A curious reader asking what the research says about whether coffee is good for you has low stakes and needs a lot of research.

Step 1 can also flag a topic in three ways. A contested topic is one where informed people disagree, so the answer shows the sides and says which way the evidence leans. A fast-moving topic is one where the right answer changed in the last year or could change soon, so the answer dates its facts. A location-dependent topic is one where the answer differs by place, so the answer says which place it is for.

The program checks three rules in order, and the first rule that fits picks the route.

1. **Heavy** if the stakes are high or the question needs a lot of research.
2. **Light** if the question needs little research.
3. **Balanced** for everything else.

Because the Heavy rule is checked first, a high-stakes question never goes Light. The topic flags do not pick the route. They change how the later steps work. For example, a one-number lookup such as the calories in a food, with low stakes, goes Light. A question about whether to replace a furnace with a heat pump, an $18,000 decision, goes Heavy because its stakes are high.

## The routes

Every model call names its exact model and effort level. Effort is a setting that controls how much the model thinks before it answers.

| Part of the scaffold | Model | Effort | Research rounds | Check step | Extra search |
|---|---|---|---|---|---|
| Steps 1 and 2 | Claude Sonnet 5 | medium | none | none | none |
| Light route | Claude Sonnet 5 | medium | 1 | Only when the stakes are medium or the topic is contested or fast-moving | No |
| Balanced route | Claude Opus 5.5 | low | 2 | Yes | No |
| Heavy route | Claude Opus 5.5 | high | Up to 3 | Yes | Yes |

On the Heavy route, the program asks the model for the one fact the answer depends on most that the notes support least well. That fact might rest on one source, an old or undated source, or none. The program then runs one more research call on that fact.

The plain model and saved instructions both ran on Claude Opus 5.5 at high effort. So the Heavy route ran its research, check and writing steps on the same model and effort level as the plain model.

## The model history

The scaffold was designed to mix the cheaper Claude Sonnet 5 with Claude Opus 5 to keep costs down. Claude Opus 5.5 arrived the week the build finished. The steps that ran on Opus moved to Opus 5.5, and the steps that ran on Sonnet 5 stayed on Sonnet 5. So the plain model and saved instructions had Opus 5.5 for everything, while the scaffold used Sonnet 5 for steps 1 and 2 and for the Light route.

## What the prompts never contain

No scaffold prompt names a specific source, fact or method that a checklist item looks for. The prompts say what to do and what kind of source to prefer, such as primary and official sources, independent tests, and peer-reviewed work. No example in a prompt is drawn from the study's 27 questions. The saved-instructions paragraph follows the same rule.

## What the program records

For every step, the program logs the model, the effort level, the tokens in and out, the web searches and page reads, the time taken, the tools allowed, and the exact prompt sent. It also logs the route, the rule that picked it, any extra Heavy search, and any skipped check step.
