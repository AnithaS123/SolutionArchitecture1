At Emirates, our performance teams had no interface for analyzing load-test data. Everything relied on deep SQL queries, and some of these queries took 22 to 26 minutes to return results. During peak traffic simulations, SQL would even stall, creating unpredictable delays in RCA and slowing down release validation.

I took ownership of this gap and built a full-stack performance insights platform using React, Node.js, and SQL Server. I partnered closely with performance engineers to understand their diagnostic workflow and designed dashboards for latency, concurrency, and high-cost query patterns. I rewrote several heavy SQL queries, added indexing strategies, and introduced pagination. These improvements reduced query response time from 22–26 minutes down to 11 minutes and stabilized performance even under large data volumes.

What started as an IBE-specific tool quickly expanded in adoption. The MRP team and the PNR Status module team also began using it because the architecture allowed each team to plug in their own database and visualize their telemetry through the same UI framework. This turned the tool from a local solution into a cross-team performance intelligence platform.

Overall, it cut 70–80% of manual SQL effort, accelerated test-cycle throughput across multiple teams, and became the core validation mechanism for every major release. Beyond the operational efficiency, the biggest impact was strengthening engineering productivity and improving system stability during peak travel seasons.



⭐ 1. STAR++ – Innovation Story (Full Version)

S — Strategic Context:
Emirates’ IBE performance tests generated massive SQL datasets during load testing. Engineers had no unified UI and depended on manual DB queries, slowing RCA, delaying releases, and creating blind spots during peak travel-season performance validation.

T — Target Outcome:
Create a modern, real-time visualization layer that converts raw performance telemetry into actionable insights — without impacting existing testing workflows — and improve release readiness velocity.

A — Architected Actions:
I took end-to-end ownership and conceptualized a full-stack solution using React, Node.js, and SQL Server. Designed REST APIs to standardize performance metrics. Implemented optimized SQL queries for large datasets. Introduced multi-view dashboards to visualize latency, query performance, and concurrency issues. Streamlined stakeholder alignment with QA, DB team, and performance engineers to ensure the tool supported their full validation cycle.

R — Business Results:
• 70–80% reduction in manual SQL effort
• Performance engineers now rely on the tool for every release cycle
• Faster issue detection → fewer last-minute blockers
• Improved stability of booking flow during peak travel seasons

+R — Reflection:
This project reinforced how internal innovation can uplift engineering maturity. It became a reusable template for future modernization initiatives and expanded my architectural role into the IBE team.

⭐ 2. STAR++ – Customer Impact Story (Full Version)

S — Strategic Context:
Performance testing teams lacked visibility into database behaviour during load tests. Every analysis required deep DB expertise → delays, context switching, and inconsistent validations. Their internal user journey was broken.

T — Target Outcome:
Improve the engineering team’s productivity and create a frictionless experience that allows them to diagnose performance regressions in seconds, not hours.

A — Architected Actions:
I directly engaged performance engineers to understand pain signals. Designed UI flows based on their diagnostic patterns. Built a lightweight, intuitive React interface powered by Node.js APIs and normalized SQL telemetry. Introduced real-time refresh cycles, data filters, and dashboards aligned to booking journey KPIs. Ran iterative demos and incorporated feedback to ensure the tool removed bottlenecks rather than adding new overhead.

R — Business Results:
• Enabled faster RCA and test-cycle efficiency
• Reduced performance verification time significantly
• Became the default tool for every release validation
• Improved internal customer satisfaction and confidence in release quality

+R — Reflection:
The biggest learning was how deeply internal teams value friction-free workflows. This project shaped my human-centered architecture style and positioned me as a trusted partner across engineering.

🌩 3. AWS Leadership Version (Ownership + Innovation + Customer Obsession)

“I noticed that our performance teams were struggling to validate load-test results because everything required manual SQL queries. Instead of accepting the limitation, I took end-to-end ownership and built a full-stack performance insights tool using React and Node.js. I worked backwards from the engineering teams’ daily pain, designed intuitive dashboards, optimized SQL queries, and delivered a system that cut manual effort by nearly 80%. It became a critical part of every IBE release cycle. This reinforced my bias for action and the impact of innovating on behalf of customers — even when it’s not explicitly assigned.”

🟦 4. Microsoft Leadership Version (Empathy + Collaboration + Growth Mindset)

“I started by deeply understanding the engineering team’s pain points — their productivity was blocked by raw SQL logs during performance testing. I collaborated openly with QA, DBAs, and performance engineers to design a tool that fit naturally into their workflow. Even though UI engineering wasn’t my original domain, I adopted a growth mindset, self-learned React, and delivered an insights platform that accelerated every release cycle. The tool improved cross-team confidence and demonstrated how inclusive design drives business performance.”

🟩 5. Google Leadership Version (Clarity + Data-Backed Innovation + Scalable Thinking)

“The core issue was signal loss — raw performance telemetry had no structured interface, and engineers couldn’t analyze patterns quickly. I introduced a data-visualization layer using React and Node.js, normalized SQL workloads, and built clear dashboards for latency, concurrency, and query time distribution. The tool provided consistent insights across all load tests and became foundational for scaling IBE modernization efforts. It showed how clarity in data representation drives high-leverage engineering outcomes.”

-------------
🔥 FOLLOW-UP QUESTIONS & ANSWERS — INNOVATION THEME
1. What made you decide to build this instead of using an existing tool?

The existing workflow relied entirely on raw SQL queries, and there was no integrated UI that matched Emirates’ IBE performance-test patterns. External tools couldn’t interpret our custom telemetry schema.
Building an internal tool allowed precision alignment with our booking flow, real-time patterns, and deep DB visibility tailored for aviation traffic behavior.

2. How did you validate that your solution was the right thing to build?

I ran short discovery sessions with performance engineers. Every conversation highlighted lost time, inconsistent queries, and blocked releases.
The validation was clear:
If we removed SQL dependency → engineers gain predictable visibility → releases become faster.
The signal was strong enough to justify a new tool.

3. What alternatives did you consider before deciding on this design?

I explored:
• Exporting SQL results into Excel dashboards
• Using off-the-shelf APM tools
• Enhancing existing test scripts

But none delivered real-time refresh, filtering by IBE patterns, or SQL telemetry correlation.
The custom architecture provided flexibility, speed, and domain-specific representation.

4. How did this change the engineering culture or workflow?

Engineers began thinking in visual performance patterns, not individual SQL queries.
It shifted performance testing from a “query-driven task” to an insight-driven workflow, making RCA faster and more consistent.
The tool turned performance testing into a self-serve capability.

5. What is the most innovative aspect of your design?

The innovation was in normalizing raw SQL performance telemetry into a real-time UI model that mapped directly to IBE transactions.
This created a bridge between database behavior and user booking experience — something they never had before.

🎯 FOLLOW-UP Q&A — CUSTOMER IMPACT THEME
6. How did you gather customer (engineer) requirements?

I treated engineers like product users.
I shadowed their test cycles, observed how they debugged latency, and mapped their most repetitive queries.
Instead of a requirement document, I built a problem-pattern map that guided the UI structure.

7. What pain points did the engineers struggle with most?

• Constant context switching between SQL queries
• No real-time view during load tests
• Delay in identifying DB bottlenecks
• Inconsistent workflows between team members

The tool removed these friction points.

8. How did you measure improvement?

We tracked three metrics:
• Time spent querying SQL per test cycle
• Time to first RCA signal
• Number of repeated queries per release

All three dropped significantly, and the team shifted from reactive debugging to predictable validation.

9. What additional features would you add with more time?

• Role-based access control
• Real-time alerts on query latency spikes
• Integration with IBE clickstream logs
• Pre-release “performance risk scoring”

These would evolve it into a predictive performance platform.

10. How did you ensure the UI matched how engineers think?

I built dashboards based on diagnostic mental models:
Latency → Concurrency → Query cost → Booking journey correlation.
Each view mirrored how engineers naturally isolate issues.
This is why adoption became effortless.

🏗 FOLLOW-UP Q&A — ARCHITECTURE DEEP-DIVE
11. Walk me through the architecture.

A lightweight three-layer design:
React UI → Node.js APIs → SQL Server.
Node cached high-frequency queries, introduced pagination, and normalized telemetry.
React consumed structured APIs and rendered real-time dashboards.
It was intentionally modular so each layer could evolve independently.

12. How did you design the API layer?

The Node.js layer served as a data abstraction service:
• Pre-processed SQL telemetry
• Applied filters, sorting, and thresholds
• Managed payload sizes
It shielded the UI from DB complexity and reduced DB load.

13. What DB bottlenecks did you face?

Large result sets caused slow fetch times.
I introduced:
• Optimized indexes
• Pagination
• Query rewriting
• Limiting high-cost diagnostic calls
This stabilized response times.

14. How did you optimize query performance?

I used:
• Index tuning
• CTEs (common table expressions)
• Partition awareness
• SQL plan analysis
Optimizing around typical load-test patterns reduced latency significantly.

15. Why React + Node?

React gave speed, modularity, and reusable UI components.
Node is event-driven — ideal for high-frequency DB calls and non-blocking I/O.
Both enabled rapid iteration and easy internal adoption.

16. How did you ensure real-time behavior without overload?

I introduced:
• Lightweight refresh intervals
• Cached recent data
• Debounced API calls
• Prioritized delta updates instead of full reloads

This kept the UI fast without hammering the DB.

17. How did you secure the tool?

• Internal network segmentation
• API-level access gating
• No direct DB exposure to the UI
• Sanitized inputs to prevent SQL injection
• Read-only DB creds with least-privilege principles

18. What caching model did you apply?

Fast-moving data was cached at the Node layer for short TTLs.
Static metadata was cached longer.
This hybrid model reduced DB round trips.

19. Did you face latency issues?

Initially yes — large queries bottlenecked the UI.
Fix: optimized indexes + pagination + result-size management.
Post-optimization, dashboard loads became consistent.

20. How would you redesign it for cloud-native scale today?

I'd rebuild it with:
• Serverless API (Azure Functions / Lambda)
• Managed SQL + read replicas
• Event Hub/Kinesis for streaming telemetry
• React with WebSockets
• Role-based access via IAM/AAD

This would turn it into a cloud-native observability platform.

⚖️ FOLLOW-UP Q&A — TRADE-OFFS
21. What trade-offs did you make?

I kept the first release lightweight.
I intentionally deprioritized:
• Authentication enhancements
• Complex alerting
• Correlation with front-end logs
The priority was speed-to-value for engineers.

22. What did you deprioritize and why?

Advanced visualization and ML-driven insights were postponed.
The mission was to solve the immediate bottleneck — repeated SQL queries and slow RCA.

23. Any features you intentionally avoided?

Raw query editors.
It would reintroduce the SQL dependency we were eliminating.

24. How would you handle 10x more data?

I’d implement:
• Horizontal scaling
• Read replicas
• SQL partitioning
• Streaming ingestion
• WebSockets for real-time updates

This would support enterprise-scale load.

🧭 FOLLOW-UP Q&A — LEADERSHIP & INFLUENCE
25. How did you drive adoption?

I demonstrated the tool during performance cycles and incorporated feedback quickly.
Early adopters became evangelists.
The tool spread organically across teams.

26. Was there resistance? How did you handle it?

Initially DBAs preferred manual queries.
I showcased how the UI reduced their workload and improved consistency.
Once they saw time savings, buy-in was immediate.

27. How did you manage cross-team alignment?

Short alignment cycles, clear communication, and incremental demos.
I treated each team as a stakeholder with unique needs.
It created shared ownership of success.

28. What leadership behaviors did you demonstrate?

• Bias for action
• Proactive innovation
• Human-centered design
• Cross-team influence
• Technical depth blended with business value

29. How did this project help you grow?

It strengthened my full-stack thinking, UI engineering confidence, and my ability to build internal tools that change workflows.
It also opened the door for my transition into the IBE modernization team.

🔥 FAILURE / RISKS
30. What went wrong?

Initial queries were too heavy and crashed the UI.
This helped me prioritize indexing and pagination.

31. What risks did you mitigate?

• DB overload during load tests
• Inconsistent RCA
• Dependence on SQL experts
• Release delays

The tool reduced operational risk significantly.

32. Any moment the project could fail?

Yes—if engineers didn’t adopt it.
Continuous feedback loops ensured the tool was designed around their workflow.

33. Biggest technical challenge?

Handling large SQL datasets while keeping UI responsive.
Solving this created the biggest productivity impact.