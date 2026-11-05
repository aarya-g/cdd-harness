# cdd-harness

How I use Claude Code day to day. It isn't a product.

## My knowledge comes first

I use Claude Code with my own skills and knowledge, because they decide how it gets used. It isn't the other way around.

Anthropic's [AI Fluency framework](https://anthropic.skilljar.com/ai-fluency-framework-foundations) backs this up: "Effective delegation requires both domain expertise and an understanding of AI capabilities." It also asks for "clearly understanding your goals and the nature of the work before involving AI."

To me, AI is an intelligence amplifier. What I know is the foundation it builds on. I set the question, decide what counts as done and make the final call.

## Marketing and CDD

Marketing and commercial due diligence (CDD) overlap. They start in the same place, with the same questions:

- Who is the customer?
- What do they want, and what will they pay?
- Who else serves them?
- Can this grow and make money?

Marketing acts on the answers. CDD tests them.

Customers alone don't prove scale, so CDD also checks margin, cash and supply.

## What I use it for

- Commercial due diligence desk research
- Product, pricing and supply numbers for my ecommerce side business
- SQL and reports
- Turning course slides into study notes

## How I use it

| Claude Code feature | How I use it |
|---|---|
| `CLAUDE.md` | One short file that points Claude to the right folder |
| Folders | Each role has its own folder: [folder tree](library/TREE.md) |
| Skills | Reusable instructions. Each task loads what it needs |
| Plan mode | I read the plan before anything changes |
| Subagents and the Agent SDK | Long jobs run in the background while I do other work. SDK runs stop for my decision |
| Bash | Claude runs my scripts and SQL, and results go into a Postgres table I can query |
| MCP | Claude reads web pages through a logged-out browser |
| Hooks | Very few, added only after the same mistake repeats |
| Memory | My corrections carry over to the next session |

## Also here

- [Decision atlas](https://cdd-atlas.vercel.app): 109 business methods, marked by whether they work for a small business. 108 come from consulting literature and one is my own. I checked 40 of 46 source claims against the originals and found none made up.
- [Sample run](SAMPLE-RUN.md): a made-up product taken through the method.
- [`library/`](library/): the runbooks that passed a privacy check. I kept client, supplier and financial data out. Sources, course notes and references stay private, so some links won't open.

AI Fluency framework: Rick Dakan, Joseph Feller and Anthropic, CC BY-NC-SA 4.0.
