# AI Engineering Case Study — Ticket Intelligence

Everything you need is in this folder.

```
Case Study - AI Ticket Intelligence.pdf   the brief — read this first
data/tickets.csv                          25,921 rows, one calendar year
evaluation/questions.json                 the five questions you will be scored on
```

## In one sentence

Build a retrieval-augmented system that turns 26,000 operational tickets into
at most 50 findings, serves them through a grounded question-answering
endpoint, and proves it does not make things up.

## What you submit

| | |
|---|---|
| `mine.py` | `python mine.py --input data/tickets.csv --out findings.json` |
| a service | `POST /ask` — question in, grounded answer with citations out |
| `evaluate.py` | runs `evaluation/questions.json` against your service and scores it |
| `README.md` | one page, and it must answer: **what did your system refuse to emit, and why?** |

## The five constraints

1. **At least two findings must come from no model call at all.** Counting and
   a step-change test is arithmetic.
2. **Refusal must be explicit.** Write the rejection rules down, report how many
   findings you discarded.
3. **Every citation must resolve** to a real ticket id that supports the claim.
4. **Running it twice must not double the output.**
5. **Report your cost** — tokens and wall-clock time for a full run.

## Anything is allowed

Any language, any framework, any model, any vector store. A numpy array is a
perfectly good vector database for fifty items, and saying so is a better answer
than installing something you do not need.

## One warning

One of the five questions has no dramatic answer. If the honest response is
"nothing unusual", your system must say so. A model that invents a finding to
fill a silence scores zero on that question however well it is written.
