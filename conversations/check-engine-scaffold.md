# Check-engine light: the scaffold

This is the scaffold conversation the article quotes in "What a Guess Can Cost at the Mechanic". The same question, asked by the same simulated user, is also shown with the [plain model](check-engine-plain-model.md).

| | |
|---|---|
| Question | "How do I fix P0420?" (task U-B-01), asked as a quick question. See [the question page](../questions/01-check-engine-p0420.md). |
| Setup | Scaffold: a short program that walks the model through seven fixed steps. See [the scaffold](../the-scaffold.md). |
| Simulated user | Answers when asked |
| Date of the conversation | September 29, 2026 |
| Outcome | The first reply asked questions. The first answer, reply 2, passed. Reply 3 also passed. |

## The conversation

The user's messages were written by GPT-6 playing the simulated user. The assistant's replies are verbatim, including their links and formatting.

### Turn 1

**User**

> How do I fix P0420?

**Assistant**

> What's the make, model, and year of your vehicle (e.g., Toyota Camry 2010, Honda Civic 2015, Ford F-150 2018), or other? What's the mileage, and any symptoms like exhaust smell, rough idle, or loss of power, or does it seem to run fine otherwise? Have you already checked freeze frame data or O2 sensor readings, has the code come back after clearing it, or is this the first time you've seen it? Are you looking to DIY this yourself, or planning to take it to a mechanic and just want to understand what's going on first?
>
> I'm assuming you want a short, practical rundown of likely causes and steps to narrow it down (not a full repair manual), no particular source preference, and that this isn't tied to a recent recall or a specific model-year issue — let me know if that's off.

### Turn 2

**User**

> 2012 Toyota Camry, 160,000 miles. It runs fine, just the check-engine light. I don’t know the freeze-frame or O2 readings, or whether the code has been cleared before. I have basic tools but no lift, and California smog is due in six weeks. What should I check before paying for a catalytic converter? A repair reference or Toyota bulletin would be helpful.

**Assistant**

> You have about six weeks, so plan backward from the smog date. The car will fail smog while the check-engine light is on. Clearing the code doesn't get around that either: it resets the car's self-tests (readiness monitors), and all but the evaporative one have to finish again before the test. Spend the next 1–2 weeks ruling out cheaper causes. If nothing turns up, the converter is the likely fault. At 160,000 miles with the engine running fine, that is a real possibility.
>
> **What to check first, roughly cheapest first**
>
> 1. **Read all the codes and the freeze-frame data.** Use an inexpensive OBD-II scanner or a free scan at a parts store. Any misfire, fuel-mixture or oxygen-sensor code comes first. Identifix: "A converter cannot be judged fairly while the engine feeds it the wrong mixture." If the scanner shows live data, write down short- and long-term fuel trim. Values far from zero point to a mixture problem rather than the converter.
> 2. **Check for Toyota bulletins by VIN.** Ask a Toyota dealer's service desk or use NHTSA's recall/TSB lookup, and ask whether the engine computer has a software update. I could not find a P0420 bulletin for a 2012 gas Camry. The ones people cite (T-SB-0094-11 and the ZE7 oil-use warranty program) are for the older 2.4L engine, not your 2.5L. That doesn't prove none exists, so the VIN check is worth doing.
> 3. **Look for exhaust leaks.** Check the manifold and the front pipe for cracks, black soot marks, or ticking when the engine is cold. A leak ahead of the rear oxygen sensor can set P0420. You don't need a lift. Ramps or a jack with jack stands are enough, but never get under a car held only by a jack. A shop smoke test is the definitive check.
> 4. **Check the rear oxygen sensor on live data.** With the engine warm, a reading stuck near 0.45 V suggests a dead sensor or wiring fault, not a bad converter. That's a much cheaper part. I'm less sure of the usual "compare front and rear sensors" test on your car. I believe the front sensor on this Camry is an air-fuel ratio sensor, not a normal switching one, so that comparison may not read the usual way. I didn't find a source that confirms it.
> 5. **Plugs and misfires.** If there are no misfire codes and it runs smoothly, this is less likely. At 160,000 miles, though, it's worth knowing when the plugs were last changed.
>
> **If it is the converter (California rules)**
> - Used converters are illegal to sell or install in California (since July 10, 2008).
> - Use a Toyota (OEM) converter or an aftermarket one with a CARB Executive Order (EO) number approved for your exact car. You can check the number in CARB's online database. Cheap federal-only converters aren't legal there. One maker's page says any aftermarket converter is fine on cars over 5 years old, but that conflicts with CARB's rules, so ignore it.
> - After the repair, drive normally for several days so the self-tests finish before you go to smog.
>
> **Sources**
> - California Bureau of Automotive Repair (BAR), OBD Test Reference. Official, primary; changes logged to Mar 2026. No interest.
> - BAR newsletter, Fall 2025, on the readiness-monitor rules. Official, primary. No interest.
> - California Air Resources Board (CARB), aftermarket catalytic converters page. Official, primary; undated. No interest.
> - Identifix, P0420 diagnosis guide. Secondary; undated, around 2026. Sells repair data to shops; low interest.
> - FIXD, P0420 article, Aug 13, 2024. Secondary. **Sells code scanners (interested).**
> - Walker Exhaust, CARB requirements page. Secondary. **Converter maker (interested); the older-car claim on it looks wrong.**
> - Go-Parts pages. **Parts seller (interested), weak; used only as a lead on older-engine bulletins.**
>
> **What I'm unsure of**
> - I could not confirm that no Toyota bulletin covers your car. Only a VIN check settles it.
> - I could not confirm your emissions warranty terms. The figure I saw was 8 years/80,000 miles, so it has very likely run out on a 2012 at 160,000 miles.
> - I could not confirm from an official page that the EO number must be visible on the converter itself, though CARB's rules make it likely.
> - BAR said in late 2025 that it may later require every self-test to finish. For now, one unfinished evaporative test still passes (as of the Fall 2025 newsletter).
> - I found no reliable California price for the converter or labor, so get two written quotes that name the part and its EO number.
>
> I assumed you wanted a short, practical checklist rather than a full repair manual, and that general repair references were acceptable. I couldn't get Toyota's factory repair manual (it's paid).

### Turn 3

**User**

> What does P0420 actually mean on my Camry? Can you link the repair reference you mentioned?

**Assistant**

> **What P0420 means on your Camry**
>
> P0420 stands for "Catalyst System Efficiency Below Threshold (Bank 1)." The engine computer has decided the catalytic converter isn't cleaning the exhaust as well as Toyota's limit requires. It works that out by comparing the oxygen sensor before the converter with the one after it. A healthy converter smooths out the oxygen changes, so the rear sensor stays fairly steady. If the rear reading starts following the front one too closely, the computer sets P0420. Your 4-cylinder has only one bank, so "Bank 1" just means the whole exhaust.
>
> The code doesn't prove the converter is bad. It means the computer's test failed. That can also happen with an exhaust leak near the sensors, a failing rear oxygen sensor, or a fuel-mixture problem, which is why those checks come before buying a converter. Your car runs fine and has no other symptoms, which fits either a worn converter at 160,000 miles or one of those cheaper faults.
>
> **The repair reference: correcting my earlier answer**
>
> I didn't find or use a Toyota factory repair manual, and I didn't find a Toyota bulletin for P0420 that covers your car. The reference I actually used is a general diagnostic guide from Identifix, a repair-data company. It explains how to diagnose P0420 on any car, not your Camry specifically:
> - [Identifix: P0420 Code, the Guide to Diagnosis and Fast Fixes](https://www.identifix.com/blogs/p0420-code-the-guide-to-diagnosis-and-fast-fixes/)
>
> For Toyota's own step-by-step procedure for your 2.5L engine, the factory source is Toyota's paid service-information site (Toyota TIS, techinfo.toyota.com). That comes from my own knowledge, not from this research, and I haven't checked its current pricing or access. The free route to bulletins is a VIN lookup on NHTSA's recall and bulletin search, or asking a Toyota dealer's service desk to check by VIN.
>
> **Sources**
> - Identifix P0420 guide. Secondary; undated, around 2026. Sells repair data to shops; low interest in which part you buy.
> - FIXD, P0420 article, Aug 13, 2024. Secondary, and the source for the code's name and list of causes. **Sells code scanners (interested).**
> - BAR, [OBD Test Reference](https://www.bar.ca.gov/obd-test-reference) and [Fall 2025 readiness-monitor newsletter](https://www.bar.ca.gov/arsc/newsletters/newsletter/fall-2025/new-obd-readiness-monitor-regulations-explained). Official, primary. No interest. These cover the smog rules from my earlier answer.
> - CARB, [Aftermarket Catalytic Converters](https://ww2.arb.ca.gov/aftermarket-catalytic-converters). Official, primary. No interest.
>
> **What I'm unsure of**
> - My description of how the computer compares the two sensors is general, and I didn't confirm it against Toyota's own documents. I also think the front sensor on your engine is an air-fuel ratio sensor rather than a standard oxygen sensor, but I couldn't confirm that. It only changes how the front sensor's live data looks on a scanner.
> - I could not confirm that no Toyota bulletin applies to your car. A VIN check will settle it.
>
> I assumed you wanted a short explanation and that general repair references are acceptable.

## How it was graded

The checklist for this question has three checks. An answer had to meet all three.

1. **Fits the person's situation.** Addresses the smog-check context and this car, after asking or being told.
2. **Gets the facts right.** Lists the standard causes (oxygen sensor, exhaust leak, converter) consistent with a recognized reference. When the user has asked what the code means, explains P0420 as catalyst efficiency below threshold.
3. **Gets the facts right.** Does not claim a specific part is the cause without a check.

Beside the checklist, the grader answered four yes-or-no questions for every answer: does it do the job, does it respect the facts the user gave, does it contain a serious accuracy error, and does it contain a serious sourcing problem. An answer passed only when every check passed, the first two answers were yes and the last two were no. [How it was graded](../how-it-was-graded.md) explains each question.

### Reply 1: not an answer

The reply asks for the car's details before giving any explanation or repair steps. A reply that only asks questions is not graded against the checklist.

### Reply 2: pass

- **All three checks passed.** The reply addresses the 2012 Camry, its 160,000 miles and the California smog deadline. It covers oxygen sensors, exhaust leaks and the converter. It makes converter failure depend on the checks before it and does not declare any part faulty.
- **Does the job: yes.** The reply gives a usable check order and says what to do before paying for a converter.
- **Respects the facts the user gave: yes.** It fits the car, the mileage, the lack of symptoms, the basic tools, the lack of a lift and the coming smog check.
- **Serious accuracy error: no.** The grader logged two small errors, a shortcut in the sensor advice and an assumed engine size. Neither is serious, because the reply tells the user to check further before buying any part.
- **Serious sourcing problem: no.** The check order and the smog advice rest on repair and regulator sources, and the reply flags the sources that sell products.

### Reply 3: pass

- **All three checks passed.** The reply explains the code for this Camry and refers back to the California smog rules. It defines P0420 as catalyst efficiency below threshold and names the converter, oxygen sensor and exhaust leaks as possible causes. It says the code does not prove the converter is bad.
- **Does the job: yes.** The user gets the code's meaning, a link to the repair reference they asked for, and what that reference covers.
- **Respects the facts the user gave: yes.** The reply contradicts nothing the user said about the car.
- **Serious accuracy error: no.** The reply assumes the Camry has a four-cylinder engine without confirming it. No part purchase or repair rests on that assumption, so the error is not serious.
- **Serious sourcing problem: no.** The linked Identifix guide supports the general explanation. The reply discloses Identifix's commercial interest and says the guide's sensor description may not fit this Camry.
