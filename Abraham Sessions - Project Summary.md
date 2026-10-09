# Abraham Sessions: Underwriting Automation Project

**Recordings:** V2026-10-08-04-28-03, V2026-10-08-05-37-06, V2026-10-08-06-48-53 (about 2 hr 15 min total)<br>
**Prepared:** October 8, 2026

> **About these notes.** Only about 15–20 minutes of the recordings is Abraham explaining the project. The rest is small talk, quiet stretches and background noise, and the mic was far from the speakers. The audio was transcribed with an offline speech-to-text model, so some of Abraham's sentences are partly garbled. Anything uncertain is flagged. The detailed walkthrough is in the **second recording, from about 15 to 40 minutes in**.

---

## What the project is

- **The goal:** Marc wants the data pulled out of an offering memorandum (OM) and put into the underwriting model automatically. Abraham was told it could take at least a month, and he planned to build one example deal as a reference.
- **Why it's on you:** Marc often has Abraham do things by hand first so he can show the developers how it's done. That suggests your version is meant to be the working example the programmers follow.
- **What Abraham showed you:** a full deal package (the OM, the seller's documents and the underwriting model). That's the same set of Cambridge Court files already in the project folder.

## What the AI has to handle

1. **Tenant charge lines in the rent roll.** Each voucher tenant shows up as at least two lines: what the tenant pays and what the subsidy pays. Some have more, depending on their charges. In one example the tenant paid about $4 and the government paid about $1,100. Abraham's point was that the government portion is guaranteed money. The AI has to add those lines together for each unit.
2. **Income levels (AMI).** Every unit is tied to an income level, such as 30%, 40%, 50%, 60% or 80%. 50% and 60% are the most common, and he's seen 80% around Sacramento. The AI has to tag each unit with the right level.
3. **Unit codes.** Each property uses its own internal unit-type codes, and some include the income level (something like "1D60" for a 60% unit). The AI needs to decode these, and the format is different for every management system.
4. **Maximum rent and HOME limits.** The model works out the maximum rent allowed for each unit, minus the utility allowance. When a property is also under the HOME program, there are high and low HOME limits, and the lower limit applies. The model's Rent and Income Matrix sheet has a note that says "need to add HOME limits," so this is a known gap.
5. **Placed-in-service date.** This is when the property started its affordable-housing period, which isn't always the year it was built or renovated. It's usually in the OM (he said CBRE OMs almost always include it), but some don't, and then it has to be found somewhere else.
6. **Vouchers vs. tax-credit limits.** Abraham explained how voucher rents compare with the income-level rent limits. *This part was hard to make out*, but it's the same voucher upside that drives Scenarios 1, 3 and 4 in the model.
7. **Rent decreases.** Some properties lowered rents in exchange for extending a contract. He called it a good deal because the money is guaranteed.

## Where the data comes from

- **CoStar** requires a login to pull data, and its login checks are stricter than the others.
- **Yardi and RealPage:** you mentioned you've already automated logging in and pulling data from both. Abraham also discussed working around RealPage OneSite's two-step login.

## Abraham's warnings about AI

- It will say "it's ready to go" when it's actually wrong, so every output has to be checked.
- It needs very detailed instructions. In his words, *"the biggest problem for us is we have to teach it,"* and Claude *"can, but you have to really teach it."*
- He mentioned **Matt**, who handed things over as finished that didn't work. *Matt may be the programmer who spent 7 months on this, so it's worth confirming.*

## Questions to ask Abraham

- [ ] Which properties use HOME limits, and where does he get the current HOME rent tables?
- [ ] Does he have a key for each management system's unit codes (OneSite, Yardi and others)?
- [ ] If the OM doesn't list the placed-in-service date, where should it come from?
- [ ] Does the AI pull rents from CoStar too, or only the OM and the seller's files?
- [ ] Who is Matt, and can you see what he built?

## Suggested next step

Map every input cell in the GPC Underwriting Model Template to where its value comes from (the OM, the T-12, the rent roll, CoStar, or an assumption), with the rules above built in. Then review that map with Abraham.
