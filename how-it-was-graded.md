# How it was graded

Every answer in every conversation was graded against a checklist written for its question before the runs, then against four yes-or-no questions. A reply passes only when it clears all of them. This page gives the grader, the rules it applied for the final grades, and the reviews that checked its work. The grader's own prompts are in [prompts/](prompts/), in the files that start with `grader_`.

## Who graded

OpenAI's GPT-6 graded every reply. It ran as `gpt-6-sol` at high effort, through OpenAI's Codex command-line tool. Effort is a setting that controls how much the model thinks before it answers. A grader from a different company was chosen because Claude models answered the questions, and [models grade their own family's answers more kindly](https://arxiv.org/abs/2604.06996).

The grader worked under four conditions.

- **It graded each reply in its own fresh session.** It saw the conversation up to and including that reply, and nothing after it.
- **It never saw which setup wrote the reply.** No setup label, file name, model name, cost or type of user reached it. The blinding is partial, because scaffold answers tend to restate the user's facts, and a grader may notice that.
- **It was told the date the conversation took place.** It judged every time-sensitive claim against that date, not the grading date.
- **It had web search,** for the lookups the rules allow. Grading ran in the two weeks after the run.

Each time, the grader received the grading rules, the question's record (its checklist and dated answer key), the conversation date, the conversation, and a set of worked examples graded by a person. It also received the facts already checked for that question and the short names it had already given to problems it found, so the same problem got the same name across replies. The grader's tokens are not counted in any setup's cost.

## Is it an answer

The grader first decides whether the reply is an answer at all. A reply is an answer when it commits to what the user asked for: the pick, the fact, the list, or the explanation. It still counts when it also asks a follow-up question. A reply is not an answer when it says it needs something from the user before it can answer, even if it gives general information along the way. A reply that only says what it will do next is not an answer either.

A reply that is not an answer gets no grades. Its tokens and turns still count toward cost, and the search for the conversation's first passing answer continues with the replies after it. The rule exists because a reply that asks for the budget should not fail for ignoring a budget it has just asked for.

## The checklist

Each question has two to four checks a good answer must meet. Each check is pass or fail, with no partial credit, and failing any one check means the reply fails. Each question has at least two kinds of check: one about the person's situation (for example, "the laptop must be $800 or less"), and one about the world (for example, whether a tax credit is still available).

Checks come in three kinds, sorted by one test: can the correct answer be written down before anyone reads the reply?

| Kind | What it means | Where the grader gets its facts |
|---|---|---|
| From the conversation | Needs no outside fact, such as "gives both sides". | The conversation only. |
| Fixed fact | The truth is the same whatever the reply says, such as a penalty rate or what a named trial found. | The question's dated answer key. |
| Depends on the answer | The truth depends on what the reply names, such as a product, a rebate or a recall. | One logged lookup per item named, at the source the check names, such as the maker's specifications or the regulator's page. |

Each line of the answer key holds one fact, the address of the page it came from, the sentence on that page word for word, the date the page was read, and the date the fact is true for. The key binds the grader. If the grader's own search contradicts the key, it still grades against the key and records the challenge separately, with its source and the line it found. The key binds because the fixed-fact checks are the traps the questions were built around, and a searching grader can land on the same out-of-date page the answering model did.

Every check is graded on its own words, both ways. A reply the words fail does not pass because it met the check's purpose some other way. A reply the words pass does not fail on a requirement the words do not state. For example, a check asking for a car's value "at about 148,000 miles" is met by a figure for that car at that mileage, whatever the reply calls the figure. When a check names a body in brackets, such as "the mainstream position (major reviews and the AHA)", the reply must present that position, but it need not name the body.

## The four yes-or-no questions

The grader answers four questions about every answer, including answers that already failed a check. For each one it writes a one-sentence reason first, then the verdict.

| Question | What it asks, in plain words | A pass needs |
|---|---|---|
| Does it do the job? | Could the user act on the reply as it stands? A list with no pick, where a pick was the job, does not do the job. Neither does an explanation that never reaches the user's question, or a number with no unit. | Yes |
| Does it respect the user's stated facts? | Did the reply respect every fact the user had stated so far that the answer turns on, such as a place, a budget, a size, a date or something to avoid? | Yes |
| Is there a serious accuracy error? | Is there a wrong claim this user would rely on and act wrongly on? | No |
| Is there a serious sourcing problem? | Does the pick, the conclusion, or a step rest on a source that does not back it up, or on no source where one is needed? | No |

A stated fact is something the user has said about their own situation, needs or limits in this conversation, up to the message the reply answers. A fact still sitting in the user's script, not yet said, is not a stated fact. Neither is the format the user asked for, which belongs to "does it do the job". A dropped secondary wish, such as a "would be nice" the pick ignores, is logged and costs nothing.

## The pass rule

A reply passes when all of these hold:

- it is an answer;
- every checklist item passes;
- it does the job;
- it respects the user's stated facts;
- it has no serious accuracy error and no serious sourcing problem;
- the grader has not vetoed it.

A conversation reached a good answer at its first passing reply, and its cost is counted up to that reply.

A veto is for a reply that would leave the user worse off in a way no check and no question names. Examples are a harmful omission, or a conclusion a competent professional would call wrong or unsafe for this user, even though every sentence is true. A veto carries one written reason and is expected to be rare. A veto used for a fault the four questions already cover is a grading error.

## What counts as a serious accuracy error

An accuracy error is serious when a user who acted on the reply would lose something that matters for their question. The user might spend money they did not need to, skip a step they need, take a step that works against them, or pick a different option than they would with the right fact. That an error "could change how the user weighs" something is not enough. The grader names what the user would do differently and what it would cost them. It quotes the reply's sentence and the source line that shows it wrong.

The test is what the error would do to this user, never a count of small errors. A stroller listed at 16.2 lb against a limit of "16 lb or less" changes nothing. Three inches on a carry-on bag can decide whether it may be carried on. Other examples of serious errors are a deadline the user would follow and get wrong, an invented source, product or trial, and a price off by enough to change the decision against the user's budget. The same price miss on an option the reply rules out is not serious. A wrong claim that is not serious is logged as a minor error and costs nothing.

## What counts as a serious sourcing problem

A sourcing problem is serious when the pick, the conclusion, or a step rests on a source that does not back it up, or on no source where the question needs one, or when the reply is a plan built from nothing. These cases follow the same test.

- **A claim the answer turns on that no cited source supports is serious, even when the claim is true.** The user cannot check it, and the reply looks better sourced than it is.
- **Only one option, or several.** A source that does not back the price or the claim behind the only option a reply offers is serious. Behind one of several options, it is minor. A main pick offered with backups counts as the only option, because the user acts on the pick.
- **Research the reply cites must match its advice.** If the cited research says to build up over time, the plan has to build up over time too.
- **A figure the reply works out itself rests on its source.** For example, "those values assume average mileage, so yours at 148,000 miles is worth about ..." rests on the guide it started from. Whether the arithmetic is right is an accuracy question.
- **An unflagged interested source behind the pick.** An interested source is a seller, installer, or maker, or a page that earns money per sale from what it recommends. The grader records on every reply whether the pick rests on one without a flag. It is a serious sourcing problem only when the user asked for tested or independent sources, or asked to avoid or flag sponsored, affiliate or paid content. Such lists are everywhere on the web, and failing every reply that used one would be too strict.

An independent tester that buys products itself and takes no money from makers for its ratings counts as independent, even when it earns some affiliate commission. An interested source needs a flag only where its interest bears on what it supports, which means where it recommends, ranks or prices the products the reply picks.

Minor sourcing findings are logged and cost nothing. They include sources that are thin or of the wrong kind, copies of one story counted as several sources, and an unflagged interested source the pick does not rest on. When a check asks for a credible source, the grader tests the kind of source, not the publisher's reputation. A named expert or institution with standing on the topic passes, such as a professional body, a university or government page, a peer-reviewed study, or a named, credentialed practitioner. An anonymous blog, a forum, a seller's page, or content with no named author or institution fails. Models agree with each other on reputation far more than they agree with human experts, so a reputation question would add a shared bias.

## The grading rules for the final grades

Each rule below applied to every reply in the final grades. Some rules were added during grading, when real replies showed a gap in the rules. Every rule was then applied to the replies already graded, so all replies were graded under the same rules.

- **One error, one dimension.** An accuracy question asks whether the claims are true, and a sourcing question asks whether the sources back them and are flagged. So a good source misread is an accuracy finding only, and an unflagged seller's page is a sourcing finding only. A fault a checklist item already covers is not also charged to the stated-facts question, so one fault never fails a reply twice.
- **Limits the reply states itself.** An honest limit, such as "this rests on one source", is not a finding, because the reply has told the user what to weigh. A false limit is a finding, such as "I couldn't confirm" when the reply's own sources confirm it.
- **What the reply could know.** Each reply is judged only on what the user had said by then, because a reply cannot use a fact it has not been given. A reply is not faulted for leaving out evidence the user excluded. The checklist items are the exception. They are graded as written, because they test whether the reply found out the facts it needed before answering.
- **The conversation counts as a whole.** A later reply may rely on sources, figures or details it gave earlier in the same conversation, and is not faulted for not repeating them. A user reads the conversation, not each reply alone.
- **A limit the user never states.** A check on a limit the user never mentions in any form, anywhere in the conversation, does not decide pass or fail. It is recorded as "found out what it needed: no" and counted separately. A limit the user gave in any form, even loosely, such as "something light" for a weight limit, is graded as written. The rule covers only facts the user alone could supply. A fact about a product or rule that the reply could look up itself is graded as written. The rule exists because the grader failed replies for missing a limit no one in the conversation ever raised.
- **Prices are judged as of the conversation's date.** The grader uses the reply's own cited source and its date first, then any other dated page near the conversation date, such as a deal post or an archived copy. A price looked up at grading time, days or weeks later, is not evidence of the price on the conversation date. When no evidence of the price on that date can be found, the price cannot be verified and does not fail the reply. The rule exists because the grader judged prices by what it found weeks later.
- **Price tolerance.** A price is checked against the source the reply cites. A different price at another seller is not an error. When the reply cites no source, the grader checks at most three pages: the maker's or official page and two major sellers. The price stands if it is within the tolerance of any of them. When the question names no tolerance, a price may be off by up to 20% of its source.
- **Ranges.** A range the reply gives for the user's case counts when its midpoint falls inside the check's or key's range, and it is no wider than the key's own range. For example, with a key of $40 to $60 a month, a reply's $35 to $55 passes, because its midpoint is $45 and its width is $20. A reply's $10 to $90 fails, because it is wider than the key's $20. A very wide range would always contain the right number and tell the user nothing.
- **A claim the grader did not check is recorded as not checked, never as correct.** The grader checks at most five claims that carry each answer, so an unchecked claim must not count in the reply's favor.
- **A method failure is recorded but never changes a grade.** It applies where a reply claims coverage or absence, such as "none found" or "this is the full list", and its method skipped an official source that exists for a weaker route. The grader must name the better source and give its address. The record shows answers that were right by a route that would not hold up.

## What else is recorded for every answer

These measures describe each answer and never decide pass or fail.

- The share of checked claims that were right, and each minor error with its source.
- A count of the sources cited, by kind: official or primary, independent, and interested.
- One or more failure codes from a fixed list: over a stated budget; ignored another stated fact; guessed a key fact instead of asking; applied a rule that has changed; invented a source, product or trial; credited a real source with a finding it did not make; gave no sources where needed; cited a source for a claim it does not contain; answered a contested question from one side; gave the wrong kind of answer; and ran out of turns. The program, not the grader, adds the last one.
- What the answer did well, in one line, even on a fail.
- The answer's word count, because [model graders favor longer answers](https://arxiv.org/abs/2404.04475).
- Whether the simulated user said it was satisfied, so the results can count conversations where the user was satisfied but no answer passed.

## The store of checked facts

Each question appears in about ten conversations, and the same claims and sources come up again and again. So each fact the grader checks is kept in a store for that question, with the line quoted from the source, the address, where on the page the line sits, and the date it was read. When a later reply makes the same claim, the grader can use the stored fact instead of searching again. At set points during grading, a Claude model tidies the store. It merges rows that state the same fact, keeps every quote, and sends any two rows that truly disagree to a person for a ruling. The prompt for the tidy-up is `prompts/claims_tidy.md`.

## The second review of every fail

The grader's fails were not taken on trust. The grader was tested against a person on 20 held-back replies. It agreed on 9 of 20, against a bar of 16 of 20. In a re-test it agreed on 4 of 9. Every time it disagreed, the grader was the stricter one.

So a Claude model reviewed every field of every reply the grader failed: each failed check, a "no" on doing the job or on stated facts, each serious error, and any veto. For each item, it went back to the source itself and marked the finding as holds, disputed, or could not verify. It checked facts only: whether the quote is on the page, whether the page says what the finding claims, and whether the source is about the same thing as the reply's sentence. It never scored and never voted, because it came from the same family as the models being graded.

The author then ruled on every disputed or unverifiable finding where overturning it would flip the reply from fail to pass or from pass to fail. The person could also overturn any grader call on a reply they saw, with a one-line reason, without knowing the setup. About 1 in 20 of the grader's passes were also spot-checked. Every overturned finding is logged with its reason.

In all, the grader saw 811 replies, 619 of them answers. The grader passed 210 of the 619. After the second review and the rulings, the final record passes 380.

This process has one gap. A pass the grader got wrong is caught only by the spot check of passes, because the second review looks only at fails.

## The blind check of 19 answers

As a check on the human rulings, the author also graded 19 answers blind, without knowing the setup or the final grade. The author passed all 19, including eight that the final grades failed: four from the plain model, three from the scaffold and one from saved instructions. On those 19, the author matched the grader on 10 and the final record on 11. So the author was more lenient than the final grades, but not kinder to the scaffold than to the other setups.

## Limits of the grading

- Checks that depend on the answer were graded by live web lookup in the two weeks after the run. Each such grade can be checked from its logged address and quote, but cannot be re-run to the same result later, because pages change.
- The dated answer keys were written by Claude models and read by a person. The grader, from a different company, could challenge a key but did not write one.
- The checklist items are only as good as their wording. A check that demands a fact a good answer could do without makes a question stricter than it should be.
- Blinding is partial, as described under "Who graded".
