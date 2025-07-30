### Write Backwards Compatible Scripts

This is one of those things that everyone agrees with, but almost no one does on a regular basis.

Seriously, ask the person reviewing your script who leaves a comment asking "What happens if this step fails? How do we recover from this?" to write the same script and they'll probably forget to do so too.

Nonetheless, it's paramount to write scripts that:
- Utilize locking + migration states to ensure you don't overwrite data that's already in its intended state.
- Check for existing writes from the script and skip over that part completely.

The examples can be very simple, for instance, if you're writing a script to add a new column and set the value for that column to a derived value. It might make the most sense to structure your script into the following parts:
- First check for whether that column exists already (In case the script failed right after the table column was created). If it doesn't, create the column.
- If the column creation block was successful, now check for all rows in the table that have an empty `NULL` value for the table.
- Populate only those rows to make sure any partial writes are still preserved even if the .

> You can obviously go one step further and try making the script atomic - I.E: If anything fails, everything is reverted. SQL Databases with their core concept of a "transaction" make this step extremely simple.

> Although the above is much more difficult to do when you're working with multiple tables or databases spanning multiple machines on something like a leader-replica setup or a geo-replicated setup.

Under no circumstance, should you write non-idempotent scripts - The outcome of the script, run no matter how many times, should always be the intended state and nothing else.

**Imp:** Not only does this step ensure your scripts are reliable, it ensures you can roll back or revert to a previous state as well. Anyone who writes a script with backwards compatibility in mind - has to implictly think about a scenario where the outcome of the script also has to be reverted, it just makes more sense that way.