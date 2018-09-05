# A Trustless Web-of-Trust &ndash; establishing identity uniqueness

Ever since the first days of PGP, the notion of a web of trust was always arround &ndash; well what else &ndash; trust. [The PGP user's guide](https://web.pa.msu.edu/reference/pgpdoc1.html) defines two questions that its web of trust should answer:
1. Does the key actually belong to whom it appears to belong?
2. Does it belong to someone you can trust to certify other keys?

As question 2 is a subjective question, the guide defines four levels of trust &ndash; unknown, untrusted, marginally trusted, or completely trusted, where the goal of these trust signatures is to establish a trust level for a specific individual, or at least trust that a specific public key represents a specific individual, by a delegation of trust along the graph of signatures. While this may be the only way to validate someone in a decentralized environment, there are some disadvantages in using subjective trust:
1. Trust is not transitive. Consider the case of a republican father and a democrat son, while the son probably trust his father more than anyone else in the world, and his father has complete confidence in president Trump, the son still might completely mistrust him.
2. Trust signatures clusterize a large community into trust subgroups, while we might want to build services that are egaliterally accessible to all community members.
3. Trust might be more easily gained for some people than others, not neccesseraly because they are more trust worthy, but rather because they have better political, social capabilities.

Within the vision of self sovereign identities, there are use cases where we need to know who is in our community, for example for decision making. When the community is big, and it can be as big as the global community of all humanity, it is not easy to define who is in the community, if there is no central authority to decide on that. In this case I claim that not only that subjective trust wont help me much in defining the boundaries of the community, but rather an objective judgement is the key for this task. I call a graph of mutual signatures, where the claims made by the signers are objective claims &ndash; a trustless web of trust. In the global community of all humanity the politician and the shy, or even the honest and the crook, should all have the same egalitarien membership within the community.

## Communities

In order to identify a community over self sovereign identities, there are two factors that need to be tested for each identity:
1. That the identity represents an individual that is in this community (same as question 1 above)
2. That there is no other identity within this community that represents the same individual

The second question is hard. It is much harder for a human being then to a computer. Even with my closest friend, I can't know for sure that he doesn't have a second identity that he is holding away from me. A computer can do quite a good job in identifying duplicates within a big database of profile images, biometric information and such, though there still isn't a perfect human identifier for which the computer cannot be fooled.

The first question, on the other hand, is quite simple for a human being and quite impossible for a computer.

> ...it is only in the realm of human consciousness that we can define what it means to be human.  
> algorithms lack any awareness about the patterns they are trained to recognize. ... only a person can recognize another person.  
> &ndash; [Democracy.earth](http://bit.ly/defpaper)

To achieve the two factors listed above, we coin the term &ndash; Uniquely Verifiable Identifiers. A UVI is an identifier (profile image, fingerprints, national ID number or anything else) that holds the following characteristics:
1. A human being with access to another individual and his UVI can evaluate with high probability, while using standard means, whether the UVI identifies the individual or not.
2. There cannot be two UVIs of the same type representing the same entity, and an algorithm, given a set of UVIs of the same type, can evaluate with high probability whether there are duplicates in the set or not.

Assuming UVIs exist, we leverage on them to create a Trustless Web-of-Trust (TWOT) as defined above. An edge in this graph from identity _p_ to identity _p'_ attest that _h_, the owner of _p_, identified and recognized that the UVI in profile _p'_ represents _h'_, the owner of _p'_. It is required that all nodes in a TWOT use the same type of UVI. This is similar to the concept of key signing parties that was used by PGP, yet without the trust element. Also, by verifying the UVI within the profile, rather than the public key, a TWOT can be used to define a community where each individual is only registered once (up to the efficiency of the UVI comparing algorithm).

## A simple example

> [catalans reach referendum day uncertain if they'll get to vote](https://www.bloomberg.com/news/articles/2017-09-30/catalans-reach-referendum-day-uncertain-if-they-ll-get-to-vote)

To demonstrate a simple use of UVI for decision making within a community, we start with an example that is only partially decentralized, as we use existing national ID numbers as UVIs. We draw the motivation for this example from the [Catalan independence referendum](https://en.wikipedia.org/wiki/Catalan_independence_referendum,_2017) held on October 1<sup>st</sup>, 2017 in Catalonia, Spain. The point of this example is that all the voters in this case are registered with a central authority (the Spanish government), yet this authority tries to prevent the referendum. The outcome was that the Spanish police confronted the Catalan voters on the day of the referendum, preventing them from voting. About 43\% of the registered voters did vote, out of which about 92\% voted in favor of Catalonia becoming an independent state. Yet it was estimated that about 15\% of the registered voters did not vote due to the police intervention. It was declared by international observers that the referendum failed to meet minimum international standards to be considered valid elections.

I claim that public identities, tested to be truthful and unique based on TWOT could have provided the Catalan people a safe and trusted way to cast their votes. In this case it is enough to identify the voters by their Spanish ID, validating their registered home address to be Catalan residents. The identification process can be achieved in a decentralized way, by people validating each other profiles, signing the ID number within the profile, to signify that they verified each other identity and home address. Given public access to this signatures anyone can verify that no one is registered twice and the referendum can be held online, without relying on any central authorities for the identification process.

## Defending sybils

Sybil identification algorithms, like [SybilGuard](https://ieeexplore.ieee.org/document/4542826/), [SybilInfer](https://www.semanticscholar.org/paper/SybilInfer%3A-Detecting-Sybil-Nodes-using-Social-Danezis-Mittal/653fbfbad9d565dd5e5e0d48b6bb32dd02e8f157), [SybilDefender](https://ieeexplore.ieee.org/document/6195572/) and others ![warning](http://latex.codecogs.com/svg.latex?%5Ccolorbox%7Bred%7D%7B%28Caution%2C%20I%20need%20to%20verify%20my%20claims%20here%20and%20check%20that%20these%20links%20are%20relevant%29%7D) are based on graph structure to differentiate between sybils (fake accounts) and honest identities. They have an underlying assumption that a sybil can create an edge in the graph with an honest identity with a lower probability than two honest identities. Under this assumption some structure differentiation is expected between sybils and clusters of honest identities. It is my claim that these differentiations are more easily identified when the underlying graph over honest nodes is random, since if this graph is clustered it may be harder to ddistinguish between sybils to partially isolated clusters of honest identities. A TWOT can serve as such a random graph. If I don't need to trust the person that I am identifying, then I can identify random people.

I therefor suggest the following procedure for defining communities with unique identities, based on the assumption that there exists a UVI that meets the above requirements with high enough probability:
1. Individuals create their own self sovereign identities and embed in their profiles a UVI that identifies them.
2. People randomely meet with other people for mutual identification &ndash; validating that the UVI in the other person profile indeed identifies him and cryptographically signing this UVI to express this validation.
3. Computer algorithms scan the web of endoresments continuously and verify that each UVI is unique in the web.
4. Any community based application that requires registration can require that only well connected identities be able to register. A well connected identity is one which UVI was endorsed by enough random identities.

Using this algorithm it will be harder for sybils to get random individuals to endorse them. Some small number of sybils will still be expected, but a herd of sybils will be hard to maintain, and easy to detect.
