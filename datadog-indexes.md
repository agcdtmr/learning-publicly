# Explain Datadog indexes in easy words

Datadog Indexes are essentially rules you set up to decide which of your raw logs are kept and made easily searchable (indexed), and for how long.

They are a core part of Datadog's "Logging without Limits" approach, which helps you manage costs by decoupling the logs you send (ingest) from the logs you pay to keep searchable (index).

Think of a Datadog Index like a high-speed filing system for a specific category of logs.


## The Key Concept: Ingestion vs. Indexing
The easiest way to understand Datadog Indexes is to distinguish between two steps:

1. Log Ingestion (Collecting Everything): Datadog encourages you to send all of your logs (from servers, applications, cloud services, etc.) into its platform. This is often the less expensive part.

2. Log Indexing (Making it Searchable): This is the process of making those logs searchable, queryable, and usable in dashboards and analytics. This is where most of the cost comes from.

**The Datadog Index is the filter and container that controls step 2.**

## How Datadog Indexes Work
- Filtering: An index is defined by a filter query (like service:web-app AND status:error). Any incoming log that matches this filter is routed to that index.

- Cost Control: By creating indexes, you can isolate your most important logs (like all error messages) and only pay to index those. You can use Exclusion Filters within an index to drop specific, low-value logs (like routine health checks) even if they matched the index's main filter.

- Retention: Each index is configured with a retention period (e.g., 7 days, 15 days, 30 days). This determines how long the indexed (searchable) logs will be kept. You can have high-value logs (errors) kept for longer and low-value logs (info messages) kept for shorter periods.

- Quota: You can set a daily quota on an index to hard-limit the volume of logs indexed per day, giving you predictable cost management.

## Example

Our app have three types of logs coming in:

1. Critical Errors: Must be searchable for 30 days.
2. User Activity: Need to be searchable for 7 days.
3. Debug Messages: Don't need to be searchable at all, but you want to keep them just in case.

We would set up two Indexes:

Index 1: "Critical-Logs"
Filter: Logs containing "status:error OR severity:critical"
Retention: 30 days

Index 2: "User-Activity"
Filter: Logs containing "tag:user-session"
Retention: 7 days

Logs that are ingested but do not match any index (like debug messages) are not indexed, so we don't pay for them to be searchable. We can, however, still choose to archive them for long-term storage and compliance.


# So remember

Datadog Index is the Rulebook and Container that decides:

- Which of your ingested logs are important enough to be made instantly searchable (Indexed).

- How long those indexed logs will be kept (Retention).

- How many logs you're willing to pay for each day (Quota).

It's the tool that gives us control over our log costs while still allowing to collect all the logs.
