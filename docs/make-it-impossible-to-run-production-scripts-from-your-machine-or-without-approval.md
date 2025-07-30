# Make it impossible to run production scripts from your machine or without approval

With the previous steps, we've anyway made it impossible to run ANY scripts from your machine to your cloud resources.

The final step to writing and running your scripts does not involve the scripts at all. It instead involves a process.

This is something almost all CI/CD Providers support: When running a script for a specific environment, say production - most importantly, you can require approvals with proofs to be submitted for the previous runsof the script on a development/staging environment.

This ensures production is only touchable once someone with enough accountability gives the needed go-ahead for it.
