# Raising the Floor on AI Answers: the study files

This repository holds the questions, checklists, simulated users, prompts, results and quoted conversations behind the Medium article "[Raising the Floor on AI Answers](ARTICLE-LINK)".

## What the study tested

The study asked whether a model can be set up so its first answer clears a quality floor, whoever asks and however they ask. It compared three setups on Anthropic's Claude models:

- **Plain model:** the model as it comes, with web search and nothing added.
- **Saved instructions:** one paragraph the model reads before every question, telling it to ask about missing details and to give a source for every key fact.
- **Scaffold:** a short program that walks the model through seven fixed steps before it answers.

The study used 27 everyday questions about money, health, cars, school, home, shopping and travel. Some were quick questions, one short line the way most people type. Others were detailed requests that spell out the situation, the limits and the form of the answer. OpenAI's GPT-6 played four kinds of user and graded every answer, against a checklist written for each question up front.

## What it found

- **The scaffold raised the floor on quick questions.** Across all four simulated users, the scaffold's first answer passed 75% of the time (54 of 72) and the plain model's 57% (41 of 72).
- **Saved instructions made sourcing far more reliable, for cents.** On the two users all three setups shared, 33% of the plain model's first answers (12 of 36) rested on a serious accuracy or sourcing error. Saved instructions cut that to 11% (4 of 36), for about 7 cents more per good answer. The scaffold cut it to 6% (2 of 36).
- **The scaffold's lead faded as the simulated users pushed back.** On those two users, by the end of the conversation the plain model and the scaffold both reached a good answer 78% of the time (28 of 36). The scaffold cost about 3.5 times as much per good answer: $0.86 against $0.24.
- **Detailed requests reversed the result.** On the 12 questions asked both ways, the plain model's first answer passed 9 of 12 as a detailed request and the scaffold's 6 of 12.

The simulated users pushed back by design, so the end-of-conversation results are a best case for the plain model. Real people may take the first answer as given.

## Start here

1. [Results](results.md): every number in the article, with its count, plus the study's fixed measures.
2. The four quoted conversations, turn by turn, with how each answer was graded:
   - [Check-engine light, plain model](conversations/check-engine-plain-model.md)
   - [Check-engine light, scaffold](conversations/check-engine-scaffold.md)
   - [Seed oils, scaffold, detailed request](conversations/seed-oils-scaffold.md)
   - [Organic lawn service, scaffold, detailed request](conversations/organic-lawn-scaffold.md)
3. [The questions](questions/README.md): all 27 questions, each with what the simulated user knew, its checklist and its answer key.
4. [How it was graded](how-it-was-graded.md): the checklist, the four yes-or-no questions, the pass rule and the checks on the grader.
5. [Simulated users](simulated-users.md): the four users and how each behaves.
6. [The scaffold](the-scaffold.md): the seven steps, the routing rule and the models each step used.
7. [Prompts](prompts/README.md): every prompt as run.
8. [Figures](figures/): the five graphics from the article.

## The setups in brief

Effort is a setting that controls how much the model thinks before it answers. All three setups had the same web search and page reader.

| Setup or step | Model | Effort |
|---|---|---|
| Plain model | Claude Opus 5.5 | high |
| Saved instructions | Claude Opus 5.5 | high |
| Scaffold, steps 1 and 2 (read the question, ask what is missing) | Claude Sonnet 5 | medium |
| Scaffold, Light route | Claude Sonnet 5 | medium |
| Scaffold, Balanced route | Claude Opus 5.5 | low |
| Scaffold, Heavy route | Claude Opus 5.5 | high |

The scaffold rates each question's stakes and how much research it needs, and a fixed rule then picks the route for the later steps. [The scaffold](the-scaffold.md) gives the rule.

The files in `prompts/` keep the names used while the study ran: "bare" is the plain model and "paragraph" is saved instructions.

## Data credits

Some questions were adapted from real first messages to chatbots in two public datasets:

- [Search Arena](https://huggingface.co/datasets/lmarena-ai/search-arena-24k), from LMArena. The user prompts are licensed under CC BY 4.0.
- [WildChat](https://huggingface.co/datasets/allenai/WildChat-1M), from the Allen Institute for AI. The dataset is licensed under ODC-BY.

Each question page says whether its question was written for this study or adapted from one of these datasets.

## License

Text, tables and figures in this repository are licensed under [CC BY 4.0](LICENSE). The questions adapted from Search Arena and WildChat keep their original licenses, credited above.

## Code

The code is available upon request.
