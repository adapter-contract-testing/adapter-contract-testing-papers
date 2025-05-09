# Third-party services: friends who mean well (until they let you down)
When dealing with third-party services, everything works fine... until something goes wrong. 
A slightly odd piece of data, an unexpected format, a relic from the web 1.0... and bam, your application stumbles.

Here are a few examples:
* A phone number starting with +33 (0) — and suddenly, your parser panics.
* A "telecom operator" field, supposedly one of (orange, sfr, bouygues, free), with a value forgotten by history: ft, neuf... we thought these entities were gone, but they survive, lurking in the shadows of databases.
* Characters in fields like age, currency, street number — experience tells us the list is endless.

So what do we do? Cry? Pray? No. We validate strongly, we parse to build domain objects, and test extensively.

💡 The winning combo:
<br> ✔️ Strict normalization and validation at the input, because if it’s (too) messy, it’s a no-go.
<br> ✔️ Tests on mountains of real data, to discover all the, let’s say, divergent cases before production finds them for you.

![Cleaning the data with an anti-corruption layer](dirty-dto-to-clean-domain-object.png)

And to go even further, discover adapter contract testing, a technique that Mathieu Cans and I are sharing with you this year at Devoxx and AlpesCraft. An elegant way to tell your web services: "You want to talk to me? Fine, but here’s the contract. And I’ll verify it."

In short, test as if your on-call peace of mind depends on it. Because... it does 😅

#### See also:
- [Adapter Contract Testing](README.md)
- [Domain Refactoring](benefit-domain-refactorability.md)
- [Dependency Migration](benefit-dependency-migration.md)