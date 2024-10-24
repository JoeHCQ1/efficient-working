# efficient-working
Ways to avoid unintentional naps in the rabbit hole

## Journal in the Ticket

This is a great example: https://github.com/defenseunicorns/uds-bundle-software-factory-nutanix/issues/186. I spent hours the Friday before with others in the call and we got a whole lot of no-where.

Monday I worked mostly on a different task to give my brain a break.

Tuesday I wrapped it up by using _writing_ and plentiful _links_ to source references to guide myself towards an solution efficiently. Now I have it working before lunch and just need to update the docs, which will be much easier with the journal.

Linking all relevant documentation is something that was common on Tangram Flex's Platform Engineering team (at least under Sears and Weiss).

## Link the relevant documentation in the Ticket

Following on the above, if you take a moment to gather the documentation known to be relevant to the work and post it to the ticket you:

- Reduce re-work (you will want to find the docs again)
- Avoid bad assumptions being baked into the task - how often is the task about doing something in a way that can't actually be done? Or at least not the way being described?
- Set yourself and others on a higher-productivity pathway. Rather than noodling on the vaguarities of logs, you and others are pre-directed to work off fairly high-trust data.

## Seperate Planning and Doing

Not to be un-agile, but planning while you do is incredibly cognitively intense, and in the end (like any multi-tasking) far slower than doing one then the other. This has shown itself incredibly true on house-projects too, not just tech. Starting to work without a plan leads to incredible waste. Agile is against planning beyond the event horizon, not planning in general. If you want to move forward, seperate planning and doing, even if that's 5 minutes planning, 10 minutes doing, repeat.

## Flashcard Rubber Duck

These are meant to be questions to ask yourself to catch common errors, of which there are so many that it's hard to remember to check all of them.

| Question | Explanation |
| :--- | :---- |
| (UDS specific) Have you bounced the Pepr watcher? | As of this writing, Pepr hangs due to a shortcoming in the Typscript runtime iirc, until that part is re-written in Go, Pepr will silently fail causing hung deploys. |
| Have you looked at the log in detail? | It takes extra concentration, but there's often more info there - note Istio has a key to understand it's logs: https://istio.io/latest/docs/tasks/observability/logs/access-log/ |
| Have you identified the component responsible? | Vague errors can be disheartening and a dulled mind unresponsive, but the first step in troubleshooting is to figure out "who don it" - can you narrow the error down to a component? |
| Do you understand what the component is trying to do? | |
| Is there any chance a secret got rotated such that Bob and Alice are operating from different truths? | Example, Nexus deploy started failing when the metrics server job tried to register because I'd deleted the namespace before a redeploy, but the external postgres preserved the original admin API key. |
| Have you googled the error? | So basic, but so important. Who knew the docker engine could fail to start because Docker Desktop added a plural where a word should be singular and borked the config.json? (2020 Stack Overflow post, experienced in 2024). |

## Reporting Team Conflict

Conflict arises. One way that has worked well to evaluate and report the severity of the interpersonal problem is to speak in terms of service degredation.

Examples:
- There's a sore point around x and y, but otherwise, interactions are fine. He still responds to my PRs, there's no tension on other topics. I.e. the API is up, but there are a couple endpoints that are down or sluggish.
- We consistently interact but there's a level of guardedness or tension in all the interactions. I.e. the entire service is in a degraded state.
- Trust is broke to the point all communications are written and emailed, and emotionally fraught from both sides. I.e. x509 errors on every comm attempt
