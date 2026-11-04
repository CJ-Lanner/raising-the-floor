# Check-engine light with code P0420

Topic: cars. Formats asked: quick question and detailed request. Task ids: U-B-01 (quick), U-F-01 (detailed).

## The question as asked

### Quick question

The users who answer when asked, give the bare minimum, or are vague opened with:

> How do I fix P0420?

The user who gives everything up front opened with:

> How do I fix P0420? 2012 toyota camry, 160k miles. check engine light is on but no symptoms, and my california smog check is due in six weeks. explain what the code means and the likely causes in order, and what i should check myself before i pay for parts or a mechanic. basic tools, no lift. a real repair reference, not a forum.

### Detailed request

The users who answer when asked, give the bare minimum, or are vague opened with:

> My 2012 Camry with 160k miles threw a P0420 code, no symptoms, and I've got a California smog check in six weeks. Can you explain what the code actually means, the likely causes in order, and what I should check myself before I pay for parts or a mechanic? Basic tools, no lift. Real repair reference, not a forum thread.

The user who gives everything up front opened with:

> My 2012 Camry with 160k miles threw a P0420 code, no symptoms, and I've got a California smog check in six weeks. Can you explain what the code actually means, the likely causes in order, and what I should check myself before I pay for parts or a mechanic? Basic tools, no lift. Real repair reference, not a forum thread. explanation first, then what to check in order. i'd rather work it out before i pay for parts or a mechanic.

## What the simulated user knew

- The car is a 2012 Toyota Camry with 160,000 miles.
- The check-engine light is on, with no symptoms.
- A California smog check is due in six weeks.
- The user is handy with basic tools and has no lift.
- The user wants to know what the code means, the likely causes in order, and what to check before paying for a catalytic converter.
- A good answer explains first, then gives an order of checks.
- The user wants enough to act on, not a manual.
- The user wants a real repair reference or a maker's bulletin, something better than a forum.
- The user would rather not spend $1,500 on a catalytic converter if the fault is a sensor.

## The checklist

A good answer had to meet every check. A check that fits the person's situation tests whether the answer used the user's own facts. A check that gets the facts right tests whether the answer is right about the world.

| # | Check | Kind | Checked against |
|---|---|---|---|
| 1 | Addresses the smog-check context and this car, after asking or being told. | Fits the person's situation | The conversation |
| 2 | Lists the standard causes (oxygen sensor, exhaust leak, converter) consistent with a recognized reference. When the user has asked what the code means, explains P0420 as catalyst efficiency below threshold. | Gets the facts right | The answer key |
| 3 | Does not claim a specific part is the cause without a check. | Gets the facts right | The conversation |

## Answer key

The key gives the code's definition and its causes from makers' service bulletins and from California's smog-check regulator. None of the bulletins is for a 2012 Camry. SAE J2012, the standard that defines the codes, is behind a paywall.

1. Toyota's own bulletin, written for the 2010 Tacoma, defines P0420 as "Catalyst System Efficiency Below Threshold", stored by the engine computer. Source: [Toyota T-SB-0161-13, October 31, 2013, page 1](https://static.nhtsa.gov/odi/tsbs/2013/MC-10132102-9999.pdf), read 2026-09-25.
2. Kia and Subaru bulletins add "Bank 1" to the same definition. Sources: [Kia TSB 160, page 1](https://static.nhtsa.gov/odi/tsbs/2016/MC-10109774-9999.pdf) and [Subaru Service Information Bulletin 09-110-23, page 1](https://static.nhtsa.gov/odi/tsbs/2023/MC-10246083-0001.pdf), both read 2026-09-25.
3. Subaru's P0420 procedure checks, in order: other stored codes first (misfire P0300 to P0304, fuel trim P0171 and P0172, oxygen and air-fuel sensor codes); then oil burning (white smoke); then the exhaust system for leaks or damage at the front pipe, the converter, the air-fuel sensor and the oxygen sensor; later, EGR and vacuum leaks and the rear oxygen sensor wiring. The procedure covers all three causes check 2 names: oxygen sensor, exhaust leak and converter. Source: [Subaru 09-110-23, steps 2 to 9, pages 1 to 7](https://static.nhtsa.gov/odi/tsbs/2023/MC-10246083-0001.pdf), read 2026-09-25.
4. Honda and Kia bulletins name two more causes. Faulty fuel injectors can set a false P0420, and engine software can be the fault, fixed by reprogramming the engine computer. The makers test before they replace the converter. Sources: [Honda Service Bulletin 18-027, March 16, 2018](https://static.nhtsa.gov/odi/tsbs/2018/MC-10133022-9999.pdf) and [Kia TSB 160, page 1](https://static.nhtsa.gov/odi/tsbs/2016/MC-10109774-9999.pdf), both read 2026-09-25.
5. In a California smog check, a 2010 or newer car fails if the check-engine light stays on with the engine running, or if a permanent trouble code is stored. Source: [California Bureau of Automotive Repair, OBD test reference](https://www.bar.ca.gov/obd-test-reference), read 2026-09-25.

## Where the question came from

The quick question is verbatim from a real message in the [WildChat dataset](https://huggingface.co/datasets/allenai/WildChat-1M). The detailed request was written for this study.
