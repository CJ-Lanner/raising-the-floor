# Check-engine light: the plain model

> Phone numbers and email addresses in the replies are replaced with [phone removed] and [email removed]. Everything else is word for word.


This is the plain-model conversation the article quotes in "What a Guess Can Cost at the Mechanic". The same question, asked by the same simulated user, is also shown with the [scaffold](check-engine-scaffold.md).

| | |
|---|---|
| Question | "How do I fix P0420?" (task U-B-01), asked as a quick question. See [the question page](../questions/01-check-engine-p0420.md). |
| Setup | Plain model: Claude Opus 5.5 with web search and nothing added |
| Simulated user | Answers when asked |
| Date of the conversation | September 29, 2026 |
| Outcome | The first answer failed. The second answer passed, so the conversation reached a good answer at reply 2. |

## The conversation

The user's messages were written by GPT-6 playing the simulated user. The assistant's replies are verbatim, including their links and formatting.

### Turn 1

**User**

> How do I fix P0420?

**Assistant**

> P0420 means **"Catalyst System Efficiency Below Threshold (Bank 1)."** The car's computer uses the oxygen sensor after the catalytic converter to judge how well the converter is working. The converter is the usual cause, but not always, so check the cheaper possibilities before you spend $500–$2,500+ on a new one.
>
> ## Step 1: Rule out cheaper causes first
>
> 1. **Check for other codes.** Misfire codes (P0300–P0308), fuel trim codes (P0171/P0172) or O2 sensor codes should be fixed first. A misfiring or rich-running engine can set P0420, and it will also ruin a new converter.
> 2. **Look for exhaust leaks** near or ahead of the rear O2 sensor, such as manifold cracks, flex pipe leaks or bad gaskets. Outside air getting in fools the sensor. Listen for ticking or puffing sounds on a cold start.
> 3. **Check the downstream (rear) O2 sensor.** A slow or failing sensor can falsely report a bad converter. Look for damaged wiring and corroded connectors.
> 4. **Check for a TSB or software update.** Many makes (Toyota, Honda, Subaru, GM and others) have service bulletins that fix false P0420 codes with an engine computer reflash. A dealer can look this up by your VIN.
>
> ## Step 2: Test the converter
>
> With an OBD2 scanner that shows live data (about $20–$40) and a fully warm engine:
>
> - **Upstream (front) O2 sensor:** should switch quickly between about 0.1 and 0.9V. That's normal.
> - **Downstream (rear) O2 sensor:** should stay fairly steady at about 0.5–0.7V.
> - **If the rear sensor switches up and down like the front one**, the converter isn't storing oxygen anymore and is probably worn out.
>
> You can also check the temperature. On a warm engine, a working converter's outlet is usually hotter than its inlet (use an infrared thermometer).
>
> ## Step 3: Replace the converter if it's actually bad
>
> - **Check your warranty.** In the US, catalytic converters are federally covered for **8 years / 80,000 miles**, and California/CARB states often allow longer. Call a dealer before you pay out of pocket.
> - **Use the right part.** An OEM or good-quality aftermarket converter lasts longer than a cheap universal one, which may set P0420 again within months. In California and other CARB states, the converter must be CARB-approved.
> - After replacing it, clear the code and drive normally for a few days so the readiness monitors can finish before any emissions inspection.
>
> ## Things to avoid
>
> - **O2 sensor spacers/"defoulers" and tuning the code away** are illegal for road vehicles under federal law and will fail inspection in many states.
> - **Catalytic converter cleaner additives** rarely fix a converter that has really failed. At best they sometimes clear a borderline case temporarily.
>
> ## Is it safe to drive?
>
> Usually yes in the short term. But if the converter is clogged, you'll notice lost power, a rotten-egg smell or a rattling sound, and then you should get it fixed soon. A flashing check engine light means a misfire, so stop driving hard right away because that can overheat the converter.
>
> If you tell me the **year, make, model, mileage** and any other codes, I can look up known TSBs and common causes for your car.

### Turn 2

**User**

> 2012 Toyota Camry, 160k miles. No symptoms, and my California smog check is due in six weeks. I don’t know if there are other codes. Can you check for bulletins and tell me what to check before I pay for a catalytic converter?

**Assistant**

> I found no Toyota bulletin that fixes P0420 on a 2012 Camry, and your car is well past the emissions warranty. That makes timing the important part: you need a clean scan and about two weeks of normal driving before the test, so start this week.
>
> ## What I found in the bulletins
>
> - **None for your car.** The 2012 Camry bulletin list I checked had nothing on catalyst, O2 sensor or engine-computer emissions issues. That list only runs through May 2020, though, so ask a Toyota dealer to check your VIN for open bulletins or campaigns. It's usually free.
> - **The well-known Camry fixes don't apply to you.** Toyota's oil-burning bulletin and extended warranty (TSB T-SB-0094-11) that links to P0420 covers the **2007–2011** 2.4L engine. Your 2012 has a different engine.
> - **Warranty has run out.** The federal converter warranty is 8 years/80,000 miles, and you're at 160k miles and 14 years.
>
> ## A correction to what I said before
>
> Your Camry's front sensor is an **air/fuel ratio sensor**, not a standard O2 sensor. It doesn't swing between 0.1 and 0.9V like I described, so compare against the **rear** sensor only. The rear sensor should stay fairly steady. If it swings up and down like the front one, the converter isn't working.
>
> ## What to check, cheapest first
>
> 1. **Get a scanner (about $20–$40) and read all codes,** including pending ones and the freeze-frame data. If a misfire, fuel trim or sensor code shows up, fix that first. It's probably the cause, and it would ruin a new converter.
> 2. **Check long-term fuel trims** on a warm engine. They should be within about ±10%. If they're off, look for a vacuum leak or a failing front sensor before blaming the converter.
> 3. **Check whether the engine burns oil.** Top it off, then check the level every 1,000 miles. Oil burning slowly poisons the converter, and it would poison a new one too.
> 4. **Look for exhaust leaks** between the engine and the rear sensor: gaskets, the flex joint and pipe joints. Black soot marks or a ticking sound on a cold start are signs.
> 5. **Test the rear O2 sensor.** At 160k miles it's probably the original. Watch its voltage:
>    - Rev the engine quickly: it should go above about 0.8V.
>    - Coast in gear with your foot off the gas: it should drop below about 0.2V.
>    - If it responds slowly or never reaches those levels, a Denso or Toyota sensor is a cheap thing to try first.
> 6. **Check how badly the converter is failing.** Scanners that read "Mode $06" data show the catalyst test result against its limit. If it's barely failing, a sensor or leak is still possible. If it's far past the limit, the converter is done.
> 7. **If it's the converter,** California requires a CARB-approved converter listed for your exact car, or a Toyota part. These cost much more than converters in other states, so get quotes early.
>
> If you have the V6, P0420 refers to one side of the engine specifically. Make sure the shop tests the right one.
>
> ## California smog timing
>
> - **Don't clear the code right before the test.** Clearing it resets the car's self-tests (readiness monitors). Since October 2025, only the EVAP monitor may be incomplete at a smog check, so an unfinished catalyst test is an automatic fail. Most cars finish these self-tests within about two weeks of normal driving.
> - **A possible 6-week plan:**
>   - Weeks 1–2: diagnose.
>   - Weeks 2–3: repair.
>   - Then about 2 weeks of normal driving.
>   - Confirm on your scanner that all monitors except EVAP say "ready" before you go.
>
> ## State repair help, if you qualify
>
> California's Consumer Assistance Program (CAP) pays up to **$1,450** toward emissions repairs on 1996 and newer cars. You'd pay about a 20% co-pay, or everything above $1,450. Household income must be at or below 225% of the federal poverty level, for example about $46k for two people.
>
> The order matters. You have to **fail the smog check first, then apply**, and you can't start repairs until you get the eligibility letter, or they won't pay. If you might qualify, take the smog test now instead of repairing first. Phone: [phone removed].
>
> If you want, send me the scanner readout (codes, fuel trims, rear sensor voltage) and I'll help you read it.
>
> Sources:
> - [2012 Toyota Camry TSBs – obd-codes.com](https://www.obd-codes.com/tsb/2012/toyota/camry/)
> - [P0420 on 2007–2011 Camry 2.4L (TSB T-SB-0094-11) – Go-Parts](https://www.go-parts.com/garage/obd-p0420-toyota-camry-2007-2011-2-4l-2az)
> - [P0420 on 2012–2017 Camry Hybrid – Go-Parts](https://www.go-parts.com/garage/obd-p0420-toyota-camry-hybrid-2012-2017-2ar-fxe-2)
> - [BAR's OBD readiness monitor regulations explained – SmogCheck.com](https://blog.smogcheck.com/news/bars-2026-obd-readiness-monitor-regulations-explained)
> - [BAR readiness monitor limits rulemaking](https://www.bar.ca.gov/pdf/regulatory-actions/readiness-monitor-limits-2024/approved-text.pdf)
> - [Apply for repair assistance – BAR CAP](https://www.bar.ca.gov/cap/repair)
> - [CAP income eligibility – BAR](https://www.bar.ca.gov/cap/income)
> - [BAR news: CAP increase to $1,450 (Jan 2025)](https://www.dca.ca.gov/newsroom/2025/bar/20250124_bar_news.pdf)

## How it was graded

The checklist for this question has three checks. An answer had to meet all three.

1. **Fits the person's situation.** Addresses the smog-check context and this car, after asking or being told.
2. **Gets the facts right.** Lists the standard causes (oxygen sensor, exhaust leak, converter) consistent with a recognized reference. When the user has asked what the code means, explains P0420 as catalyst efficiency below threshold.
3. **Gets the facts right.** Does not claim a specific part is the cause without a check.

Beside the checklist, the grader answered four yes-or-no questions for every answer: does it do the job, does it respect the facts the user gave, does it contain a serious accuracy error, and does it contain a serious sourcing problem. An answer passed only when every check passed, the first two answers were yes and the last two were no. [How it was graded](../how-it-was-graded.md) explains each question.

### Reply 1: fail

- **Check 1 failed.** The reply gives general advice for any car. It asks for the year, make, model and mileage only in its last line, and never asks about an inspection deadline. The second review agreed that the check's words were not met.
- **Checks 2 and 3 passed.** The reply defines P0420 and names oxygen sensors, exhaust leaks and the converter as possible causes. It calls the converter the usual cause but asks for checks before treating any part as the cause.
- **Does the job: yes.** The grader found a usable general explanation and check order.
- **Respects the facts the user gave: yes.** The user had given only the code, and the reply contradicts nothing.
- **Serious accuracy error: yes.** The grader found the front-sensor test wrong for this Camry. The reply says the front sensor "should switch quickly between about 0.1 and 0.9V", but this Camry's front sensor is an air-fuel ratio sensor that does not behave that way. The grader said the test could lead the user to buy a sensor they do not need. The second review disputed this mark, because the user had not yet named the car and the test fits the ordinary front sensor many cars use. The reply failed on check 1 and on sourcing either way, so the mark stood.
- **Serious sourcing problem: yes.** The reply gives a full diagnosis and replacement plan, with voltage tests, part prices and a warranty term, and names no source at all. The question needs a repair reference the user can check before spending money on parts. The second review agreed.

### Reply 2: pass

- **All three checks passed.** The reply addresses the 2012 Camry, its 160,000 miles and the California smog deadline. Its check order covers sensor faults, exhaust leaks and the converter. It makes every part recommendation depend on a diagnostic check first.
- **Does the job: yes.** The reply gives a bulletin finding, an ordered set of checks and a smog-check plan the user could follow.
- **Respects the facts the user gave: yes.** It uses the car, the mileage, the lack of symptoms, the unknown other codes and the six-week smog deadline.
- **Serious accuracy error: no.** The grader found two small errors, in the bulletin list and in a date for the readiness rules. Neither changes the checks the user should run or the smog-check rule the user must meet, so neither is serious.
- **Serious sourcing problem: no, after the second review.** The grader marked one step as unsupported: "If it's far past the limit, the converter is done." The cited parts-seller page says only that a reading over the limit means the computer's catalyst test failed, and nothing about how far over. The second review agreed the page does not support that step. But the step comes sixth, after other codes, fuel trims, oil burning, exhaust leaks and the rear sensor, and the same page says the converter is the likely cause once those check out. A user who follows the reply's order buys a converter only after the cheaper causes are ruled out, so the unsupported step costs the user nothing. The final grade is no serious sourcing problem.
