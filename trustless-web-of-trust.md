# A Trustless Web-of-Trust &ndash; establishing identity uniqueness

Ever since the first days of PGP, the notion of a web of trust was always arround &ndash; well what else &ndash; trust. The PGP user's guide<sup>[1](#fn1)</sup> define two questions that its web of trust should answer:
1. Does the key actually belong to whom it appears to belong?
2. Does it belong to someone you can trust to certify other keys?

As question 2 is a subjective question, the guide defines four levels of trust &ndash; unknown, untrusted, marginally trusted, or completely trusted, where the goal of these trust signatures is to establish a trust level for a specific individual, or at least trust that a specific public key represents a specific individual, by a delegation of trust along the graph of signatures. While this may be the only way to validate someone in a decentralized environment, there are some disadvantages in using subjective trust:
1. Trust is not transitive. Consider the case of a republican father and a democrat son, while the son probably trust his father more than anyone else in the world, and his father has complete confidence in president Trump, the son still might completely mistrust him.
2. Trust signatures clusterizes a large community into trust subgroups, while we might want to build services that are egaliterally accessible to all community members.
3. Trus might be more easily gained for some people than others, not neccesseraly because they are more trust worthy, but rather because they have better political, social capabilities.


> ...it is only in the realm of human consciousness that we can define what it means to be human. - Democracy.earth

Democracy.earth propose to use self recorded videos as a proof of identity. In their white paper \cite{DemocracyEarth:WhitePaper} they recommend that the person being recorded will say out loud a series of identifiers that can be used to singularly identify him. They claim that as algorithms lack awareness, only a person can recognize another person, or in other words . More formally, they differentiate between \emph{Reputation} - a social indicator that a given identity is to be trusted, and \emph{Singularity} - an individual indicator that certifies an identity is uniquely tied to a single person. This is somewhat similar to definition \ref{definition:public-identity-attributes} above, differentiating between public identity being truthful or unique, though maybe while truthfulness can be seen as an objective statement, it seems the Democracy.earth refer to subjective trust when they define \emph{Reputation}. They propose a process where random entities that are already accepted as trusted entities are given pairs of videos as described above and are asked to vote whether they represent the same person or not. These voting are then combined into a singularity score for the identity.

We propose in this section a more direct approach, where we still rely on the human ability to recognize another human, yet we rely on algorithms to perform the exhaustive check whether a specific identifier is singularly used. For this purpose we define the following.

\begin{definition}[Recognizable unique identifiers]
We define a \emph{Recognizable unique identifier} (RUI) to be an identifier that holds the following characteristics:
\begin{itemize}
\item \emph{Recognizable}: a human being with access to an entity (another human being) and its RUI can evaluate with high probability, while using standard means, whether the RUI identifies the entity or not.
\item \emph{Unique}: there cannot be two RUIs of the same type representing the same entity, and an algorithm, given a set of RUIs of the same type, can evaluate with high probability whether there are duplicates in the set or not.
\end{itemize}
\qqed
\end{definition}

Assuming RUIs exist, we leverage on them to define a scheme where human beings identify each other. We note that without trusted third parties, a single identification step says nothing about the identified entity, as there is no reason to trust the identifier. We therefor suggest the construction of a public web of trust and discuss next how trusted groups can be evaluated from such a graph. A public web of trust can only suggest which RUI are truthful. We rely on algorithmic registrars to make sure that within a single registry each RUI is also unique.

\begin{definition}[Public web of identity trust]
A public web of identity trust (PWOIT) is a public web of trust where trust edges over the graph between $p$ and $p'$ attest that $h$, the owner of $p$, identified and recognized that the RUI in profile $p'$ represents $h'$, the owner of $p'$. It is required that all nodes in a PWOIT use the same type of RUI.
\qqed
\end{definition}

\ouri{TBD - further elaborate how the two steps complement each other and why both are required}

\ouri{TBD - implementation issues (signing the RUI and its containing profile together, holding multiple RUIs, types of registrars, zero knowledge for accessing registries without compromising privacy, democratically choosing registrars, approvals as tokens so they can be revoked (both from the PWOIT and from the registrar))}

\ouri{TBD - on the benefits of PWOIT - a randomized graph with very high conductance, tying to the preventing sybil infiltration paper}

\subsection{A simple example - a local semi-decentralized e-democracy}

\href{https://www.bloomberg.com/news/articles/2017-09-30/catalans-reach-referendum-day-uncertain-if-they-ll-get-to-vote}{catalans reach referendum day uncertain if they'll get to vote}

\href{https://www.google.co.il/search?rlz=1C1GCEA_enIL767IL767&ei=w61dW6-BEMqGaqCpoKgJ&q=catalonia+referendum+police+preventing+reaching+the+polling+stations&oq=catalonia+referendum+police+preventing+reaching+the+polling+stations}{many more links}

To demonstrate a simple use of RUI for e-democracy, we start with an example that is only partially decentralized, as we use existing national ID numbers as RUI. It is localized, as national IDs can uniquely identify entities only withing a single nation. We draw the motivation for this example from the \href{https://en.wikipedia.org/wiki/Catalan_independence_referendum,_2017}{Catalan independence referendum} held on October 1\textsuperscript{st}, 2017 in Catalonia, Spain. What characterize this referendum is the fact that all the voters are registered Spanish citizens, yet the government of Spain did not approve of this referendum. The result was that on the referendum day Spanish police confronted the Catalan voters. About 43\% of the registered voters did vote, out of which about 92\% voted in favor of Catalonia becoming an independent state. Yet it was estimated that about 15\% of the registered voters did not vote due to the police intervention. It was declared by international observers that the referendum failed to meet minimum international standards to be considered valid elections.

We claim that public identities, tested to be truthful and unique based on PWOIT could have provided the Catalan people a safe and trusted way to cast their votes. In this case it is enough to identify the voters by their Spanish ID, validating their registered home address to be Catalan residents. The identification process can be achieved in a decentralized way, by people validating each other profiles, signing the ID number within the profile, to signify that they verified each other identity and home address. Given that these profiles can be stored in a blockchain that supports smart contracts, a single, localized, yet public and open sourced smart contract can supply uniqueness tokens to each profile, by comparing the given ID number to all preceding numbers and signing the number and its profile, if the same number did not register before. In this case, since a person can validate another person ID card with high probability, the chances of someone having more than one ID number is minimal and an algorithm can verify that each number registered only once, the Spanish ID number is therefor a RUI. Using a PWOIT can therefor uniquely identify valid voters, fending off Sybils, without relying on centralized authorities in the identification process.

\subsection{Global e-democracy, using biometrics as RUI}
\ouri{TBD - after I read more about biometrics}

\subsection{Security and threats analysis}
Verifying uniqueness of on-line identities in a decentralized way seems like almost an impossible mission. Like all other published methods, the scheme proposed here is surely not a bulletproof scheme and is far from guarantying 100\% uniqueness. Yet it is not intended to be. Our goal is to make it harder to create a fake identity than a truthful and unique identity, making Sybil operators pay for any Sybil they create. In this section we discuss the vulnerabilities of our scheme and our take on each of them.

<a name="fn1">1</a>: https://web.pa.msu.edu/reference/pgpdoc1.html
