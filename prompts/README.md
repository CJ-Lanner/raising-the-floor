# The prompts as run

This folder holds every prompt the study sent to a model, copied word for word from the files the run used. The file names and the text inside them use the study's working names. "Bare" is the plain model and "paragraph" is saved instructions. The simulated users are "upfront" (gives everything up front), "forthcoming" (answers when asked), "dripfeed" (gives the bare minimum) and "vague". "Must-have checks" are the checklist, and "resolved" means the conversation reached a good answer.

Text in square brackets, such as `[first message]` or `[notes]`, is a slot. The program fills each slot before it sends the prompt. When a prompt mentions `rubric.md`, it means the grading rules, which are written up in [how-it-was-graded.md](../how-it-was-graded.md).

## What each file is for

| File | Used by | What it is for |
|---|---|---|
| `bare_system.md` | Plain model | The one-line system prompt the plain model ran with. |
| `paragraph_system.md` | Saved instructions | The one paragraph that replaces the plain model's line. Nothing else changes. |
| `scaffold_system.md` | Scaffold | The system prompt for every scaffold step. |
| `scaffold_step1_read_intent.md` | Scaffold, step 1 | Reads the question and fills in a form: the kind of question, what is stated and missing, the stakes, how much research it needs, and topic flags. |
| `scaffold_step2_elicit.md` | Scaffold, step 2 | Asks the user for the missing facts that would change the answer, in one message. |
| `scaffold_step4_retrieve.md` | Scaffold, step 4 | The first round of research: search, keep sources, take notes with a source beside each claim. |
| `scaffold_step4_retrieve_later_rounds.md` | Scaffold, step 4 | Added to the research prompt on the second and third rounds, with the notes so far. |
| `scaffold_heavy_exposed_question.md` | Scaffold, Heavy route | Finds the one fact the answer depends on most that the notes support least well. |
| `scaffold_heavy_extra_retrieve.md` | Scaffold, Heavy route | One extra research call on that fact. |
| `scaffold_step5_verify.md` | Scaffold, step 5 | Checks the claims that would change the answer, once each, for evidence they are wrong or out of date. |
| `scaffold_step6_constant_tools_prefix.md` | Scaffold, step 6 | The opening line of the writing step, telling the model not to search. |
| `scaffold_step6_compose.md` | Scaffold, step 6 | Writes the answer from the checked notes, with sources and what the model is unsure of. |
| `scaffold_step7_adapt.md` | Scaffold, step 7 | Revises the answer after the user replies. |
| `persona_core.md` | Simulated users | The instructions every simulated user shares: stay in character, never invent a fact, and when to stop. |
| `persona_upfront.md` | Simulated user who gives everything up front | How that user behaves. |
| `persona_forthcoming.md` | Simulated user who answers when asked | How that user behaves. |
| `persona_dripfeed.md` | Simulated user who gives the bare minimum | How that user behaves. |
| `persona_vague.md` | Vague simulated user | How that user behaves. |
| `grader_instructions.md` | Grader | The steps the grader follows for each reply. |
| `grader_output_schema.json` | Grader | The form the grader fills in for each reply, as a JSON schema. |
| `grader_worked_examples.md` | Grader | Replies graded by a person, which show the grader where the line between a serious and a minor error sits. |
| `claims_tidy.md` | Store of checked facts | Tidies the store of facts the grader has already checked for a question: merges duplicates and flags real conflicts. |
| `claims_tidy_schema.json` | Store of checked facts | The form that tidy-up fills in, as a JSON schema. |

The scaffold's step 3, which picks the route, is a rule in the program and has no prompt. [the-scaffold.md](../the-scaffold.md) explains every step.

## What changed, and what is not here

- **One heading rewritten.** The first line of `grader_worked_examples.md` is a file heading. The program strips it before sending, so the model never saw it. It held a working note and now reads "Worked examples for the grader".
- **Two working notes removed.** A dated note in `grader_instructions.md` and one in `grader_output_schema.json` are gone. Neither changed an instruction. Everything else is exactly as sent.
- **Two inputs are built at run time and are not files here.** The grader also received an excerpt of the grading rules and the question's own record (its checklist and answer key). Both are written up in [how-it-was-graded.md](../how-it-was-graded.md) and the [question pages](../questions/README.md).
