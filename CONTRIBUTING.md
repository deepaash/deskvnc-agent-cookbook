# Contributing to the DeskVNC agent cookbook

Thanks for being here. This is a small, copy-pasteable cookbook that
gathers the cheatsheets, config snippets, and worked examples that
make the [DeskVNC](https://github.com/psmux/DeskVNC) MCP server easy
to wire up from any agent. The gists in this repository are the unit
of contribution: each one is a single self-contained file.

## What a good change looks like

A useful change is one of:

* A new gist that is genuinely additive, on a topic the existing six
  do not cover. Examples that would fit: a `dvv` one-liner set for a
  specific CI runner, a worked loop for a specific OS task, a
  `dvv` integration recipe for a new MCP client.
* A fix to an existing gist. Typos, a stale command, a wrong path,
  a wrong error code, an em dash that slipped in.
* A new section in the README that links to a new gist.

What is out of scope for this repository:

* Any change to the DeskVNC project itself. Those land in
  <https://github.com/psmux/DeskVNC>, not here.
* Any claim that the cookbook itself supports. The cookbook links
  into DeskVNC; it does not implement or wrap it.

## House rules

* **Every factual claim is traceable to a source.** Either the
  DeskVNC README, `docs/AGENTS.md`, `docs/ARCHITECTURE.md`, the
  shipped skill at `skills/deskvnc/SKILL.md`, or another gist in
  this cookbook. If you cannot point at a source, leave the claim
  out.
* **No em dashes, no en dashes, no horizontal bars.** A single
  ASCII hyphen is fine for compound modifiers and bullet lists.
  Use commas for parenthetical asides, colons to introduce an
  explanation, parentheses for genuinely optional asides, a full
  stop and a new sentence when a thought needs its own weight, and
  the word "to" for ranges.
* **Stay positive.** The cookbook is a reference for the things
  the agent plane does. It does not list what is missing, what is
  planned, or what is in the project's "not yet implemented" file.
* **One long-lived peer, one limb per call.** The cookbook
  describes the pattern the project documents. Do not propose a
  different loop in a gist.
* **Public gists only.** The cookbook links to public gists so
  the links are useful in the open. Do not paste a secret gist URL
  into a pull request.

## Pull request shape

* One gist change per pull request is fine. One README change per
  pull request is fine. Two unrelated changes belong in two pull
  requests.
* The pull request description should name the source for every
  factual claim it adds. A single line per claim is enough.
* If your change is to a gist, the pull request should also link
  to the gist on `https://gist.github.com/deepaash/`.

## Reporting an error

If a gist is wrong, open an issue that points at the line and the
correct reading. A link to the source that says so is the fastest
way to get the change made.

## Code of conduct

Be patient with newcomers. The point of the cookbook is to lower
the floor for the next person to wire `dvv` into their agent.
