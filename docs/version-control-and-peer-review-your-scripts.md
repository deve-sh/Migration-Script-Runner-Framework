# Version Control and Peer Review your scripts

This is one of those things that doesn't happen easily when transitioning from a "script-as-you-go" setup to a "script-methodically" setup.

Senior Engineers with a lot of context of the system, even when they realize the value of peer reviews and version control, do not use it to get things done quickly (Let's be honest - If we were in the boat we would do the same).

I'm here to tell you that it's the most simple thing you can do to minimize errors and problems from your script. Most errors and catastrophic failures stem from wrong assumptions made during the writing process or simple things like transaction handling that's missing.

Most of these errors can be eliminated the moment you have a second eye reading through your code.
This also forces the script-writer to ensure human-readability of their code over optimized and short blocks of code.

- Make your scripts as verbose and human-understandable as possible.
- Have a junior engineer go through and review your code. If they can understand the script in a couple of gos, you've achieved good readability.
- Version control your scripts in a separate repository or as part of the repository that serves the business use case for what you're writing the script.
- If you're transitioning to or already on an infrastructure-as-code setup, make sure to version control and get reviews in the repository concerned with that.

Most scripts you write will not need repeat usage to justify committing them to a repository, but it's not a bad idea regardless because it gives you historical context and accountability of changes in your database schema or infrastructure.