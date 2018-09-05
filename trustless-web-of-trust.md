# A Trustless Web-of-Trust &ndash; establishing identity uniqueness

Ever since the first days of PGP, the notion of a web of trust was always arround &ndash; well what else &ndash; trust. The PGP user's guide<sup>[1](#fn1)</sup> define two questions that its web of trust should answer:
1. Does the key actually belong to whom it appears to belong?
2. Does it belong to someone you can trust to certify other keys?

As question 2 is a subjective question, the guide defines four levels of trust &ndash; unknown, untrusted, marginally trusted, or completely trusted, where the goal of these trust signatures is to establish a trust level for a specific individual, or at least trust that a specific public key represents a specific individual, by a delegation of trust along the graph of signatures. While this may be the only way to validate someone in a decentralized environment, there are some disadvantages in using subjective trust:
1. Trust is not transitive. Consider the case of a republican father and a democrat son, while the son probably trust his father more than anyone else in the world, and his father has complete confidence in president Trump, the son still might completely mistrust him.
2. Trust signatures clusterizes a large community into trust subgroups, while we might want to build services that are egaliterally accessible to all community members.
3. Trust might be more easily gained for some people than others, not neccesseraly because they are more trust worthy, but rather because they have better political, social capabilities.

Within the vision of self sovereign identities, there are use cases where we need to know who is in our community, for example for decision making. When the community is big, and it can be as big as the global community of all humanity, it is not easy to define who is in the community, if there is no central authority to decide on that. In this case I claim that not only that subjective trust wont help me much in defining the boundaries of the community, but rather an objective judgement is the key for this task. I call a graph of mutual signatures, where the claims made by the signers are objective claims &ndash; a trustless web of trust. In the global community of all humanity the politician and the shy, or even the honest and the crook, should all have the same egalitarien membership within the community.

## Communities

In order to identify a community over self sovereign identities, there are two factors that need to be tested for each identity:
1. That the identity represents an individual that is in this community (same as question 1 above)
2. That there is no other identity within this community that represents the same individual

The second question is hard. It is much harder for a human being then to a computer. Even with my closest friend, I can't know for sure that he doesn't have a second identity that he is holding away from me. A computer can do not a bad job in identify duplications within a big database of profile images, biometric information and such, though there still isn't a perfect human identifier for which the computer cannot be fooled.

The first question, on the other hand, is quite simple for a human being and quite impossible for a computer.

> ...it is only in the realm of human consciousness that we can define what it means to be human.  
> algorithms lack any awareness about the patterns they are trained to recognize. ... only a person can recognize another person.  
> &ndash; Democracy.earth<sup>[2](#fn2)</sup>

To achieve the two factors listed above, we coin the term &ndash; Uniquely Verifiable Identifiers. A UVI is an identifier (profile image, fingerprints, national ID number or anything else) that holds the following characteristics:
1. A human being with access to another individual and his UVI can evaluate with high probability, while using standard means, whether the UVI identifies the individual or not.
2. There cannot be two UVIs of the same type representing the same entity, and an algorithm, given a set of UVIs of the same type, can evaluate with high probability whether there are duplicates in the set or not.

Assuming UVIs exist, we leverage on them to create a Trustless Web-of-Trust (TWOT) as defined above. An edge in this graph from identity _p_ to identity _p'_ attest that _h_, the owner of _p_, identified and recognized that the UVI in profile _p'_ represents _h'_, the owner of _p'_. It is required that all nodes in a TWOT use the same type of UVI. This is similar to the concept of key signing parties that was used by PGP, yet without the trust element. Also, by verifying the UVI within the profile, rather than the public key, a TWOT can be used to define a community where each individual is only registered once (up to the efficiency of the UVI comparing algorithm).

## A simple example

> [catalans reach referendum day uncertain if they'll get to vote](https://www.bloomberg.com/news/articles/2017-09-30/catalans-reach-referendum-day-uncertain-if-they-ll-get-to-vote)

To demonstrate a simple use of UVI for decision making within a community, we start with an example that is only partially decentralized, as we use existing national ID numbers as RUI. We draw the motivation for this example from the [Catalan independence referendum](https://en.wikipedia.org/wiki/Catalan_independence_referendum,_2017) held on October 1<sup>st</sup>, 2017 in Catalonia, Spain. What characterize this referendum is the fact that all the voters are registered Spanish citizens, yet the government of Spain did not approve of this referendum. The result was that on the referendum day Spanish police confronted the Catalan voters. About 43\% of the registered voters did vote, out of which about 92\% voted in favor of Catalonia becoming an independent state. Yet it was estimated that about 15\% of the registered voters did not vote due to the police intervention. It was declared by international observers that the referendum failed to meet minimum international standards to be considered valid elections.

We claim that public identities, tested to be truthful and unique based on TWOT could have provided the Catalan people a safe and trusted way to cast their votes. In this case it is enough to identify the voters by their Spanish ID, validating their registered home address to be Catalan residents. The identification process can be achieved in a decentralized way, by people validating each other profiles, signing the ID number within the profile, to signify that they verified each other identity and home address. Given public access to this signatures anyone can verify that no one is registered twice and the referendum can be held online, without relying on any central authorities for the identification process.

## Defending sybils
\ouri{TBD - on the benefits of PWOIT - a randomized graph with very high conductance, tying to the preventing sybil infiltration paper}


\subsection{Security and threats analysis}
Verifying uniqueness of on-line identities in a decentralized way seems like almost an impossible mission. Like all other published methods, the scheme proposed here is surely not a bulletproof scheme and is far from guarantying 100\% uniqueness. Yet it is not intended to be. Our goal is to make it harder to create a fake identity than a truthful and unique identity, making Sybil operators pay for any Sybil they create. In this section we discuss the vulnerabilities of our scheme and our take on each of them.

<a name="fn1">1</a>: https://web.pa.msu.edu/reference/pgpdoc1.html
<a name="fn2">2</a>: http://bit.ly/defpaper
