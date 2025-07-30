# Framework for running critical scripts

One of the truths of software engineering, especially for the folks on the backend and devops side of things, is that you'll inevitably need to run scripts, a LOT of scripts.

These can be scripts to spin up database instances, VM Instances or migration scripts to change the data type of a table column or migrate an entire table view from one to another with added or derived bits of information. Normal day-to-day stuff.

As someone at an early-stage startup, it is super easy to simply SSH into the instances responsible for running your database or your server and make changes directly. This approach, while convenient, acts as a reit of passage for engineers who inevitably terminate the only database process running without a backup or accidentally kill the server process and have no idea how to spin the process back up again taking down business-critical functionality with them.

The next natural step is to isolate the instances on which you run the scripts and instead write scripts on your machine to "connect" to these databases and run the neat migration commands. This works for most large companies as well, and I've seen very successful companies continue to use this approach with additions such as code reviews and version control. BUT there are still problems: Compliance + The lack of assurance that the scripts will proceed to completion.

A minor power cut, a minor network issue can throw the entire script off to oblivion and turn your data from readable chunks into a nightmare that even the best engineers wouldn't want to touch and fix with a ten-foot-pole. All while product managers scratch their heads trying to make sense of what to tell your users on why they aren't able to see their step counts anymore and why the calorie burn count shows Infinity.

This repository is a set of documents (My opinions) and frameworks for running migration scripts. Read best on GitHub.

> Do note that these are from the perspective of an engineer who's worked at small-and-mid-sized companies. If they seem off to you, feel free to raise a PR to correct or add context to the documents.

### What this repository isn't

This doesn't have guides on how to write scripts, obviously. This repository acts as a framework for writing "better" scripts than what an engineer at an early-stage startup might be exposed to.

There are a few universally accepted facts about scripts which I don't even need to mention, such as:
- Use type-safe query-builders and ORMs when dealing with database migrations.
- Use official libraries to ease things up like infra spinup, and abstract away API details to ensure humans understand what's being written.
- Write scripts for humans to read and review, if that means putting the whole thing in one function for cohesion then so be it.

### Index

- [Write Backwards Compatible Scripts](./docs/write-backwards-compatible-scripts.md)
- [Version Control and Peer Review your scripts](./docs/version-control-and-peer-review-your-scripts.md)
- [Setup the framework for running scripts - Secrets Management, Infra Management etc](./docs/setup-the-framework-for-running-scripts.md)
- [Adjust the setup to minimize bandwidth and network usage](./docs/adjust-the-setup-to-minimize-bandwidth-and-network-usage.md)
- [Make it impossible to run production scripts from your machine or without approval](./docs/make-it-impossible-to-run-production-scripts-from-your-machine-or-without-approval.md)

### Contributions

As stated above, these documents are created by someone who has only worked at Small and Mid-sized tech companies and has seen how these processes evolve.

This repository serves as a blueprint for not just the community, but for me to make sure I don't make the same lazy mistakes as a younger me did.

If you have insights that the community could use to write and run better scripts, feel free to fork this repository and raise a PR with your insights.