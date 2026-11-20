<!-- This file is generated from the published API contract — do not edit by hand. -->

# stlabs command reference

One section per command. `stlabs <command> --help` prints the same usage and examples; the rule for running a command again is only here.

## `access grants search`

Find who has been given access

Usage: `stlabs access grants search`

Examples:

```
# Find access an administrator gave
stlabs access grants search --given-by admin
# Find who has one permission
stlabs access grants search --permission '<permission>'
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `access groups children add`

Nest a group in another

Usage: `stlabs access groups children add <group> <child> [--idempotency-key <key>]`

Examples:

```
# Nest one group inside another
stlabs access groups children add <group> <child>
```

Check read: `stlabs access groups get <group>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs access groups get <group>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `access groups children remove`

Take a group out of another

Usage: `stlabs access groups children remove <group> <child> [--idempotency-key <key>]`

Examples:

```
# Take a group out of another
stlabs access groups children remove <group> <child>
```

Check read: `stlabs access groups get <group>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs access groups get <group>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `access groups create`

Create a group

Usage: `stlabs access groups create [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `name`.

Examples:

```
# Create a group
stlabs access groups create --name 'Finance approvers'
```

Check read: `stlabs access groups search`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs access groups search` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`. The record can be on a later page, so read every page.

## `access groups get`

Show a group

Usage: `stlabs access groups get <group>`

Examples:

```
# Show a group, what it can do and where it is nested
stlabs access groups get <group>
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `access groups members add`

Put someone in a group

Usage: `stlabs access groups members add <group> <person> [--idempotency-key <key>]`

Examples:

```
# Put someone in a group
stlabs access groups members add <group> <person>
```

Check read: `stlabs access groups members list <group>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs access groups members list <group>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`. The record can be on a later page, so read every page.

## `access groups members list`

List the people in a group

Usage: `stlabs access groups members list <group>`

Examples:

```
# List the people in a group
stlabs access groups members list <group>
# Find someone in a group
stlabs access groups members list <group> --search maria
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `access groups members remove`

Take someone out of a group

Usage: `stlabs access groups members remove <group> <person> [--idempotency-key <key>]`

Examples:

```
# Take someone out of a group
stlabs access groups members remove <group> <person>
```

Check read: `stlabs access groups members list <group>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs access groups members list <group>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`. The record can be on a later page, so read every page.

## `access groups permissions add`

Give a group a permission

Usage: `stlabs access groups permissions add <group> <permission> [--idempotency-key <key>]`

Examples:

```
# Give a group a permission
stlabs access groups permissions add <group> '<permission>'
```

Check read: `stlabs access groups get <group>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs access groups get <group>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `access groups permissions remove`

Take a permission away from a group

Usage: `stlabs access groups permissions remove <group> <permission> [--idempotency-key <key>]`

Examples:

```
# Take a permission away from a group
stlabs access groups permissions remove <group> '<permission>'
```

Check read: `stlabs access groups get <group>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs access groups get <group>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `access groups search`

List groups

Usage: `stlabs access groups search`

Examples:

```
# List groups
stlabs access groups search
# Find a group by name
stlabs access groups search --search finance
# List the groups a person is in
stlabs access groups search --member <person>
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `access groups update`

Rename a group

Usage: `stlabs access groups update <group> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: none.

Examples:

```
# Rename a group
stlabs access groups update <group> --name 'Finance leads'
# Change what a group is for
stlabs access groups update <group> --description 'Signs off on spend'
# Remove a group's description
stlabs access groups update <group> --clear description
```

Check read: `stlabs access groups get <group>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs access groups get <group>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `access people list`

List people and their roles

Usage: `stlabs access people list`

Examples:

```
# List people
stlabs access people list
# Find someone by name or email
stlabs access people list --search maria
# List people who can do one thing
stlabs access people list --has-access '<permission>'
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `access people permissions add`

Give a person a permission

Usage: `stlabs access people permissions add <person> <permission> [--idempotency-key <key>]`

Examples:

```
# Give a person a permission
stlabs access people permissions add <person> '<permission>'
```

Check read: `stlabs access people permissions get <person>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs access people permissions get <person>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `access people permissions get`

See what a person can do

Usage: `stlabs access people permissions get <person>`

Examples:

```
# See what a person can do
stlabs access people permissions get <person>
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `access people permissions remove`

Take a permission away from a person

Usage: `stlabs access people permissions remove <person> <permission> [--idempotency-key <key>]`

Examples:

```
# Take a permission away from a person
stlabs access people permissions remove <person> '<permission>'
```

Check read: `stlabs access people permissions get <person>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs access people permissions get <person>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `access permissions list`

List permissions

Usage: `stlabs access permissions list`

Examples:

```
# List what people can be given
stlabs access permissions list
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `access roles list`

List roles

Usage: `stlabs access roles list`

Examples:

```
# List the roles people can have
stlabs access roles list
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `access roles members add`

Give someone a role

Usage: `stlabs access roles members add <role> <person> [--idempotency-key <key>]`

Examples:

```
# Make someone an admin
stlabs access roles members add admin <person>
```

Check read: `stlabs access roles members list <role>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs access roles members list <role>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`. The record can be on a later page, so read every page.

## `access roles members list`

List the people in a role

Usage: `stlabs access roles members list <role>`

Examples:

```
# See who is an admin
stlabs access roles members list admin
# Find an admin by name
stlabs access roles members list admin --search maria
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `access roles members remove`

Take a role away from someone

Usage: `stlabs access roles members remove <role> <person> [--idempotency-key <key>]`

Examples:

```
# Take the admin role away from someone
stlabs access roles members remove admin <person>
```

Check read: `stlabs access roles members list <role>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs access roles members list <role>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`. The record can be on a later page, so read every page.

## `approvals approve`

Approve an approval

Usage: `stlabs approvals approve <approval> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: none.

Examples:

```
# Approve a request
stlabs approvals approve <approval> --comment 'Fine by me'
```

Check read: `stlabs approvals get <approval>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs approvals get <approval>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `approvals checklist set`

Tick or untick a task's step

Usage: `stlabs approvals checklist set <approval> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `checked`, `item`.

Examples:

```
# Tick a step
stlabs approvals checklist set <approval> --item <step> --checked
# Untick a step
stlabs approvals checklist set <approval> --item <step> --checked=false
```

Check read: `stlabs approvals get <approval>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs approvals get <approval>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.
- `WRITE_SUCCEEDED_READ_FAILED`: the change landed. Do not run it again.

## `approvals get`

Get an approval, task or form

Usage: `stlabs approvals get <approval>`

Examples:

```
# Read an approval, task or form
stlabs approvals get <approval>
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `approvals inputs submit`

Answer a form

Usage: `stlabs approvals inputs submit <approval> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `values`.

Examples:

```
# Answer a form
stlabs approvals inputs submit <approval> 'values: {laptop: Mac}'
```

Check read: `stlabs approvals get <approval>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs approvals get <approval>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `approvals list`

List approvals

Usage: `stlabs approvals list`

Examples:

```
# List what is waiting for you
stlabs approvals list
# List approvals you asked for
stlabs approvals list --lens requested_by_me
# List approvals that were rejected
stlabs approvals list --status rejected
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `approvals reject`

Reject an approval

Usage: `stlabs approvals reject <approval> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: none.

Examples:

```
# Reject a request
stlabs approvals reject <approval> --comment 'Over budget'
```

Check read: `stlabs approvals get <approval>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs approvals get <approval>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `approvals tasks complete`

Complete a task

Usage: `stlabs approvals tasks complete <approval> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: none.

Examples:

```
# Mark a task done
stlabs approvals tasks complete <approval> --comment 'Finished'
```

Check read: `stlabs approvals get <approval>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs approvals get <approval>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `people availability get`

Get someone's availability

Usage: `stlabs people availability get <person>`

Examples:

```
# Read someone's working hours
stlabs people availability get <person>
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `people availability search`

Check who can take a ticket now

Usage: `stlabs people availability search [flags] ['<body>']`

Required fields: `people`.

Examples:

```
# Check who can take a ticket now
stlabs people availability search --people '<person>,<person>'
# Include how many tickets each person has open
stlabs people availability search --people '<person>,<person>' --open-tickets
```

Retrying:

- This reads with a POST, which `stlabs` does not retry. Running it again is safe, so run it again yourself when the response says `retryable`.

## `people availability set`

Replace someone's availability

Usage: `stlabs people availability set <person> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `timezone`, `unavailable_reason`, `unavailable_until`, `working_hours`.

Examples:

```
# Replace someone's working hours with one Monday window and end any pause
stlabs people availability set <person> 'timezone: Europe/London, unavailable_reason: null, unavailable_until: null, working_hours: [{start_day_of_week: 0, start: "09:00", end_day_of_week: 0, end: "17:00"}]'
```

Check read: `stlabs people availability get <person>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs people availability get <person>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `queues create`

Create a queue

Usage: `stlabs queues create [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `name`.

Examples:

```
# Create a queue
stlabs queues create --name '<queue name>'
# Create a queue with a description and a time zone
stlabs queues create --name '<name>' --description '<purpose>' --timezone Europe/London
```

Check read: `stlabs queues get <queue>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs queues get <queue>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.
- `WRITE_SUCCEEDED_READ_FAILED`: the change landed. Do not run it again.

## `queues get`

Get one queue

Usage: `stlabs queues get <queue>`

Examples:

```
# Read one queue
stlabs queues get <queue>
# Read a queue with its ticket counts
stlabs queues get <queue> --stats
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `queues operators add`

Add someone to a queue

Usage: `stlabs queues operators add <queue> <person> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `role`.

Examples:

```
# Add someone to a queue
stlabs queues operators add <queue> <person> --role member
# Make someone a lead of a queue
stlabs queues operators add <queue> <person> --role lead
```

Check read: `stlabs queues operators list <queue>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs queues operators list <queue>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`. The record can be on a later page, so read every page.

## `queues operators list`

List who works a queue

Usage: `stlabs queues operators list <queue>`

Examples:

```
# List who works a queue
stlabs queues operators list <queue>
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `queues operators remove`

Take someone out of a queue

Usage: `stlabs queues operators remove <queue> <person> [--idempotency-key <key>]`

Examples:

```
# Take someone out of a queue
stlabs queues operators remove <queue> <person>
```

Check read: `stlabs queues operators list <queue>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs queues operators list <queue>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`. The record can be on a later page, so read every page.

## `queues search`

Find queues

Usage: `stlabs queues search [flags] ['<body>']`

Required fields: none.

Conditional fields: `operator.person` is required with `operator`.

Examples:

```
# Find queues by name
stlabs queues search --name support
# Find the queues someone leads
stlabs queues search --operator person=<person> --operator role=lead
```

Retrying:

- This reads with a POST, which `stlabs` does not retry. Running it again is safe, so run it again yourself when the response says `retryable`.

## `queues setdefault`

Make a queue the default

Usage: `stlabs queues setdefault <queue> [--idempotency-key <key>]`

Examples:

```
# Send new tickets to this queue unless routing picks another
stlabs queues setdefault <queue>
```

Check read: `stlabs queues get <queue>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs queues get <queue>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `queues update`

Change a queue

Usage: `stlabs queues update <queue> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: none.

Conditional fields: `awaiting_reply.close_hours` is required with `awaiting_reply`; `awaiting_reply.reminder_hours` is required with `awaiting_reply`; `awaiting_reply.then` is required with `awaiting_reply`; `marked_resolved.auto_close_hours` is required with `marked_resolved`; `service_levels.first_response` is required with `service_levels`; `service_levels.resolution` is required with `service_levels`.

Examples:

```
# Rename a queue
stlabs queues update <queue> --name '<new name>'
# Say when a quiet requester is reminded and the ticket is closed
stlabs queues update <queue> --awaiting-reply close-hours=48 --awaiting-reply reminder-hours=24 --awaiting-reply then=cancel
# Stop routing tickets here
stlabs queues update <queue> --auto-routing=false
```

Check read: `stlabs queues get <queue>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs queues get <queue>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.
- `WRITE_SUCCEEDED_READ_FAILED`: the change landed. Do not run it again.

## `tickets bulk update`

Change many tickets at once

Usage: `stlabs tickets bulk update [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `tickets`.

Examples:

```
# Assign several tickets to one person
stlabs tickets bulk update --tickets '<ticket>,<ticket>' --assignee me
# Move several tickets to another queue
stlabs tickets bulk update --tickets '<ticket>,<ticket>' --queue '<queue>'
```

Check read: `stlabs tickets list`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets list` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`. The record can be on a later page, so read every page.

## `tickets comments create`

Add a comment to a ticket

Usage: `stlabs tickets comments create <ticket> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `body`.

Examples:

```
# Comment on a ticket
stlabs tickets comments create <ticket> --body '<comment>' --visibility public
# Comment with the fields written as one body string
stlabs tickets comments create <ticket> 'body: <comment>, visibility: public'
```

Check read: `stlabs tickets comments list <ticket>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets comments list <ticket>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`. The record can be on a later page, so read every page.
- `WRITE_SUCCEEDED_READ_FAILED`: the change landed. Do not run it again.

## `tickets comments delete`

Delete a comment you wrote

Usage: `stlabs tickets comments delete <ticket> <comment> [--idempotency-key <key>]`

Examples:

```
# Delete a comment
stlabs tickets comments delete <ticket> <comment>
```

Check read: `stlabs tickets comments list <ticket>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets comments list <ticket>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`. The record can be on a later page, so read every page.

## `tickets comments list`

Read a ticket's conversation

Usage: `stlabs tickets comments list <ticket>`

Examples:

```
# Read the comments on a ticket
stlabs tickets comments list <ticket>
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `tickets comments update`

Change a comment you wrote

Usage: `stlabs tickets comments update <ticket> <comment> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `body`.

Examples:

```
# Change a comment
stlabs tickets comments update <ticket> <comment> --body '<new comment>'
```

Check read: `stlabs tickets comments list <ticket>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets comments list <ticket>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`. The record can be on a later page, so read every page.
- `WRITE_SUCCEEDED_READ_FAILED`: the change landed. Do not run it again.

## `tickets counts get`

Count tickets by state, queue or priority

Usage: `stlabs tickets counts get [flags] ['<body>']`

Required fields: `group_by`.

Examples:

```
# Count tickets by state
stlabs tickets counts get --group-by state
# Count open tickets by queue
stlabs tickets counts get --group-by queue --state open
```

Retrying:

- This reads with a POST, which `stlabs` does not retry. Running it again is safe, so run it again yourself when the response says `retryable`.

## `tickets create`

File a ticket

Usage: `stlabs tickets create [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `title`.

Conditional fields: exactly one of `requester_email`, `requester`.

Examples:

```
# File a ticket, leaving the queue and priority to routing
stlabs tickets create --title '<title>' --requester me
# File a ticket with a longer description
stlabs tickets create --title '<title>' --requester me --description '<details>'
# File a ticket with the body written as one string
stlabs tickets create 'requester_email: <your email>, title: <short title>'
```

Check read: `stlabs tickets list`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets list` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`. The record can be on a later page, so read every page.
- `WRITE_SUCCEEDED_READ_FAILED`: the change landed. Do not run it again.

## `tickets filters delete`

Delete a saved filter

Usage: `stlabs tickets filters delete <saved_filter> [--idempotency-key <key>]`

Examples:

```
# Delete a saved filter
stlabs tickets filters delete <filter>
```

Check read: `stlabs tickets filters list`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets filters list` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `tickets filters list`

List your saved filters

Usage: `stlabs tickets filters list`

Examples:

```
# List your saved filters
stlabs tickets filters list
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `tickets filters rename`

Rename a saved filter

Usage: `stlabs tickets filters rename <saved_filter> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `name`.

Examples:

```
# Rename a saved filter
stlabs tickets filters rename <filter> --name '<new name>'
```

Check read: `stlabs tickets filters list`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets filters list` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `tickets filters reorder`

Put your saved filters in order

Usage: `stlabs tickets filters reorder [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `saved_filters`.

Examples:

```
# Put your saved filters in a new order, naming every id from the list
stlabs tickets filters reorder --saved-filters 12,9,4
```

Check read: `stlabs tickets filters list`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets filters list` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `tickets filters setdefault`

Make a saved filter your default

Usage: `stlabs tickets filters setdefault <saved_filter> [--idempotency-key <key>]`

Examples:

```
# Make a saved filter your default
stlabs tickets filters setdefault <filter>
```

Check read: `stlabs tickets filters list`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets filters list` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `tickets get`

Get one ticket

Usage: `stlabs tickets get <ticket>`

Examples:

```
# Read one ticket
stlabs tickets get <ticket>
# Open a ticket in your web browser
stlabs tickets get <ticket> --web
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `tickets list`

List and filter tickets

Usage: `stlabs tickets list`

Examples:

```
# List your open tickets
stlabs tickets list --requester me --state open
# List tickets assigned to you
stlabs tickets list --assignee me
# Find tickets that mention a word
stlabs tickets list --search vpn
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `tickets nudge`

Remind the assignee

Usage: `stlabs tickets nudge <ticket> [--idempotency-key <key>]`

Examples:

```
# Remind the assignee to reply
stlabs tickets nudge <ticket>
```

Check read: `stlabs tickets get <ticket>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets get <ticket>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.
- `WRITE_SUCCEEDED_READ_FAILED`: the change landed. Do not run it again.

## `tickets priorities list`

Read your organization's priorities

Usage: `stlabs tickets priorities list`

Examples:

```
# List the priorities a ticket can have
stlabs tickets priorities list
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `tickets queues list`

Read your organization's queues

Usage: `stlabs tickets queues list`

Examples:

```
# List the queues you can file into
stlabs tickets queues list
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `tickets relationships create`

Link two tickets

Usage: `stlabs tickets relationships create <ticket> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `target`, `type`.

Examples:

```
# Link a ticket to one it duplicates
stlabs tickets relationships create <ticket> --target <other> --type <type>
# Link two tickets and say why
stlabs tickets relationships create <ticket> --target <other> --type <type> --note '<why>'
```

Check read: `stlabs tickets relationships list <ticket>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets relationships list <ticket>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `tickets relationships list`

Read a ticket's linked tickets

Usage: `stlabs tickets relationships list <ticket>`

Examples:

```
# List the tickets linked to a ticket
stlabs tickets relationships list <ticket>
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `tickets relationships types list`

Read the kinds of link between tickets

Usage: `stlabs tickets relationships types list`

Examples:

```
# List the kinds of link between tickets
stlabs tickets relationships types list
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `tickets similar list`

Find tickets like this one

Usage: `stlabs tickets similar list <ticket>`

Examples:

```
# Find tickets like one you are reading
stlabs tickets similar list <ticket>
# Include similar tickets that are still open
stlabs tickets similar list <ticket> --include-open
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `tickets states list`

Read your organization's states

Usage: `stlabs tickets states list`

Examples:

```
# List the states a ticket can be in
stlabs tickets states list
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `tickets transition`

Move a ticket through its life

Usage: `stlabs tickets transition <ticket> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `to.state`.

Examples:

```
# Resolve a ticket
stlabs tickets transition <ticket> --state resolved
# Resolve a ticket and say why
stlabs tickets transition <ticket> --state resolved --reason '<why>'
```

Check read: `stlabs tickets get <ticket>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets get <ticket>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.
- `WRITE_SUCCEEDED_READ_FAILED`: the change landed. Do not run it again.

## `tickets translations get`

Translate a ticket's text

Usage: `stlabs tickets translations get <ticket> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `text`.

Examples:

```
# Translate a ticket's title into English
stlabs tickets translations get <ticket> --text title
# Translate a comment into German
stlabs tickets translations get <ticket> --text 'comment:<id>' --language de-DE
```

Check read: `stlabs tickets get <ticket>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets get <ticket>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `tickets translations list`

Read a ticket's translations

Usage: `stlabs tickets translations list <ticket> [flags] ['<body>']`

Required fields: `texts`.

Examples:

```
# Read what is stored for a ticket's title and description
stlabs tickets translations list <ticket> --texts title,description
```

Retrying:

- This reads with a POST, which `stlabs` does not retry. Running it again is safe, so run it again yourself when the response says `retryable`.

## `tickets update`

Change a ticket's fields

Usage: `stlabs tickets update <ticket> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: none.

Examples:

```
# Change a ticket's title
stlabs tickets update <ticket> --title '<new title>'
# Add a follower
stlabs tickets update <ticket> --add-follower '<person id>'
# Remove a ticket's priority
stlabs tickets update <ticket> --clear priority
```

Check read: `stlabs tickets get <ticket>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs tickets get <ticket>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.
- `WRITE_SUCCEEDED_READ_FAILED`: the change landed. Do not run it again.

## `workflows availability set`

Let everyone in your organization run a workflow, or stop

Usage: `stlabs workflows availability set <workflow> [flags] ['<body>'] [--idempotency-key <key>]`

Required fields: `open_to_everyone`.

Examples:

```
# Let everyone run a workflow
stlabs workflows availability set '<workflow id>' --open-to-everyone
```

Check read: `stlabs workflows get <workflow>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs workflows get <workflow>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `workflows delete`

Delete a workflow

Usage: `stlabs workflows delete <workflow> [--idempotency-key <key>]`

Examples:

```
# Delete a workflow
stlabs workflows delete '<workflow id>'
```

Check read: `stlabs workflows get <workflow>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs workflows get <workflow>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `workflows dependencies list`

List what a workflow calls and what calls it

Usage: `stlabs workflows dependencies list <workflow>`

Examples:

```
# Show what calls a workflow
stlabs workflows dependencies list '<workflow id>'
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `workflows disable`

Turn a workflow off

Usage: `stlabs workflows disable <workflow> [--idempotency-key <key>]`

Examples:

```
# Turn a workflow off
stlabs workflows disable '<workflow id>'
```

Check read: `stlabs workflows get <workflow>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs workflows get <workflow>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `workflows enable`

Turn a workflow on

Usage: `stlabs workflows enable <workflow> [--idempotency-key <key>]`

Examples:

```
# Turn a workflow on
stlabs workflows enable '<workflow id>'
```

Check read: `stlabs workflows get <workflow>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs workflows get <workflow>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `workflows get`

Get one workflow

Usage: `stlabs workflows get <workflow>`

Examples:

```
# Show one workflow
stlabs workflows get '<workflow id>'
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `workflows grants add`

Give a person or group access to a workflow

Usage: `stlabs workflows grants add <workflow> <grantee_type> <grantee> <permission> [--idempotency-key <key>]`

Examples:

```
# Let a group run a workflow
stlabs workflows grants add '<workflow id>' group '<group id>' run
```

Check read: `stlabs workflows grants list <workflow>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs workflows grants list <workflow>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `workflows grants groups list`

List groups that can be given access to a workflow

Usage: `stlabs workflows grants groups list <workflow>`

Examples:

```
# Find a group to give access to
stlabs workflows grants groups list '<workflow id>' --search Support
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `workflows grants list`

List who has access to a workflow

Usage: `stlabs workflows grants list <workflow>`

Examples:

```
# See who has access to a workflow
stlabs workflows grants list '<workflow id>'
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `workflows grants remove`

Take away a person's or group's access to a workflow

Usage: `stlabs workflows grants remove <workflow> <grantee_type> <grantee> <permission> [--idempotency-key <key>]`

Examples:

```
# Take a group's access away
stlabs workflows grants remove '<workflow id>' group '<group id>' run
```

Check read: `stlabs workflows grants list <workflow>`.

Retrying:

- `stlabs` never retries this command itself.
- Run it again only when the response says `retryable`, and with the same `--idempotency-key`.
- After `outcome_unknown`, or on a 5xx response or a network failure, the change may have landed. Run `stlabs workflows grants list <workflow>` first. If it finds nothing, ask the person before running it again, with a new key after `IDEMPOTENCY_OUTCOME_UNKNOWN`.

## `workflows inputs get`

See what starting a workflow asks for

Usage: `stlabs workflows inputs get <workflow>`

Examples:

```
# See what a run asks for
stlabs workflows inputs get '<workflow id>'
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `workflows list`

List workflows

Usage: `stlabs workflows list`

Example:

```
stlabs workflows list
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `workflows runnability get`

Check whether a workflow can run

Usage: `stlabs workflows runnability get <workflow>`

Examples:

```
# Check a workflow can run
stlabs workflows runnability get '<workflow id>'
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `workflows runnable search`

Find a workflow to run

Usage: `stlabs workflows runnable search --q <text>`

Examples:

```
# Find a workflow to run
stlabs workflows runnable search --q laptop
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `workflows runs events list`

List what happened in a run

Usage: `stlabs workflows runs events list <run>`

Examples:

```
# Show what happened in a run
stlabs workflows runs events list '<run id>'
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `workflows runs get`

Get a run

Usage: `stlabs workflows runs get <run>`

Examples:

```
# Show one run
stlabs workflows runs get '<run id>'
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `workflows runs list`

List runs

Usage: `stlabs workflows runs list`

Examples:

```
# List recent runs
stlabs workflows runs list
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.

## `workflows versions get`

Get one version of a workflow

Usage: `stlabs workflows versions get <workflow> <version>`

Examples:

```
# Show one published version
stlabs workflows versions get '<workflow id>' 3
```

Retrying:

- `stlabs` retries this read itself, so do not loop on it.
- Try again later only when the response says `retryable`.
