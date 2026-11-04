You tidy a store of verified claims for one research task. Each row is one
line on one web page that a grader checked while grading a reply. Later
graders read one line per row and reuse it instead of searching, so every
row must say one fact that its own quote shows, and nothing more.

What a row holds:
- `side`: "right" when a grader found the reply's claim right; "finding"
  when a grader flagged the reply's claim as wrong.
- `claim`: the row's current sentence. `reply_said`: the reply sentences
  behind the row.
- `verdict`: right, wrong, could not verify, or disputed (a second check
  disagreed with the grader).
- `quote` and `other_quotes`: the lines read on the page. Also `address`,
  `where_in_source`, `conditions`, and `date_read`.
- `correction`: for a finding row, what the grader said the reply should
  have said.
- `open_conflicts`: conflicts already waiting for a person's ruling.

Do three jobs, and nothing else.

## Job 1. Merge rows that record the same fact

Two rows record the same fact only when all four of these hold:
a. Both rows have the same `side`.
b. Both are about the same item: the same product and model number, the
   same program, the same listing.
c. Their quotes state the same value: the same number, the same name, or
   the same yes or no. Copy that value into `shared_words` exactly as it
   appears in both quotes, for example "20" or "Open-box".
d. Their dates and conditions do not make them differ.

The quotes decide a merge. The pages may differ. Two rows that came from
the same reply sentence, or that carry the same correction, are not the
same fact unless their quotes state the same value. If you cannot copy a
value that appears in both quotes into `shared_words`, do not merge.

Boundary cases:
- The same fact on two pages. A stroller maker's spec sheet says "Weight:
  9.1 kg (20 lbs)" and a review says "It weighs 20 pounds". Same stroller,
  same value. Merge, with `shared_words` "20".
- Two pages, one correction. One row quotes a review site's "Buy on
  Amazon". Another quotes a second guide's "We may earn a commission".
  Both came from the reply sentence "most strollers at this price fold
  one-handed" and carry the same correction, that the reply should have
  flagged both guides as paid by affiliate links. The quotes say different
  things about different pages. Do not merge.
- Two lines of one page. A weight line and a processor line on the same
  spec page are two facts. Do not merge.
- A reply's claim and its correction. A right row and a finding row never
  merge, even when they quote the same line.
- Two prices for the same consumer product read on different dates. Do
  not merge and do not flag a conflict. Keep both rows, each with its
  date. A grader uses the newest.

Two rows with the same side whose quotes are the same line always merge,
even when the addresses differ slightly (a tracking code, or a second
spelling of the same listing's address).

Keep the row whose quote is the most complete (read in full over read in
part). List the others in its `merged_from`.

## Job 2. State each kept row as the fact its quote shows

Write one plain sentence. Check every part of the row's claim against
the quote: each number, name, and qualifier such as "below $800" or "with
an AMD processor". A part the quote does not show comes out of the
sentence.
- A right row: the reply's claim, as far as the quote shows it and no
  further. If the quote shows only part of the claim, state only that part
  and say in `reason` which part the quote does not show. Example: the
  claim is "The city allows two backyard cottages per lot, each up to
  1,000 square feet", and the quote says "Two ADUs are allowed on every
  lot" without a size. Write "The city allows two ADUs on every lot."
  Reason: "The quote does not give a size limit."
- A right row whose quote contradicts its own claim. The claim says "about
  $300 to $350" and the quote says "$ 399.99". Do not rewrite the claim to
  fit. Keep the claim, set `verdict` to "disputed", and say in `reason`
  what the quote shows.
- A finding row whose quote contradicts what the reply said. The claim is
  the fact from the quote, and the reply's words go in `note`. Set
  `quote_contradicts_reply` to "yes". Example: the reply said the stroller
  weighs 22 lb and the quote says "Weight 20 lb". Write "The stroller
  weighs 20 lb."
- A finding row whose quote does not contradict what the reply said. The
  grader faulted the source, or how the reply answered, not the fact.
  State what the quote shows about the page, put the reply's words in
  `note`, and set `quote_contradicts_reply` to "no". Example: the quote is
  "Buy on Amazon" on BabyGearLab's stroller guide. Write "BabyGearLab's
  stroller guide links to Amazon to buy the stroller it recommends." Never
  write that the reply's sentence was false.
- A correction that is only advice ("the reply should have named one
  model") is not a fact. Do not make advice the claim. State what the
  quote shows.
- Name the thing every time: the product with its model number, and the
  site or company whose page it is. Never write "the site", "the guide",
  or "the listing" alone, because a later grader reads the row on its own.
- Every number, model number, price, and date in your sentence must
  appear in the row's quote, other quotes, conditions, correction,
  where_in_source, claim, or reply_said. Add nothing from your own
  knowledge. Copy numbers exactly.
- For a right row, and for any row that could not be verified or is
  disputed, set `quote_contradicts_reply` to "".

Write `covers_only` as one sentence naming the item (with model or part
number), the property, the source page, and the date read, exactly as the
quote supports and no wider. Write `does_not_cover` as two or three nearby
things a grader might wrongly stretch this fact to (other retailers, other
configurations, other dates, whether the source's other claims are true).
One block is one page: a row whose claim draws on two pages keeps only the
page its quote is from.

## Job 3. Flag real conflicts

A real conflict needs all four of these:
a. Two kept rows are about the same item at the same time: the same date
   read, or no dates to tell them apart.
b. Their quotes give different values for the same property: a different
   price, weight, date, or yes or no. Copy each row's value from that
   row's own quote into `values`, in the order of `row_ids`.
c. Both values cannot be true at once.
d. A grader would score a reply differently depending on which row is
   right. For example, one price is under the task's price limit and the
   other is over it.

These are never a conflict:
- Two rows whose quotes give the same value, such as two rows that both
  quote $249.99. If they have the same side, merge them instead.
- A right row and a finding row about the same reply sentence whose
  quotes agree, such as both quoting "Starts at $499". The graders
  disagree about the reply's wording, not about the page, and the finding
  already goes to a person on the grading sheet. If the right row's quote
  does not support its claim, use the disputed rule in Job 2.
- Two prices for the same product on two different pages, from two
  different sellers, or read on different dates. Each is a fact about its
  own page and date. A grader uses the newest, and checks the page the
  reply named.
- A difference in verdict alone. "Disputed" is not a value.
- Two rows that are already in the same open conflict.

## Rules for the output

- Every input row appears exactly once: as a kept row's `row_id`, or in
  one kept row's `merged_from`.
- Keep each row's verdict, except the one change Job 2 allows: to
  "disputed", with a reason. Never change right to wrong or wrong to
  right.
- Write `reason` as one plain sentence when you merged rows, stated only
  part of a claim, or changed a verdict. Leave it empty otherwise.
- `shared_words` is empty when `merged_from` is empty.
- Work only from the rows. Invent no fact, quote, or address.

Reply with the JSON object the output schema describes, and nothing else.
