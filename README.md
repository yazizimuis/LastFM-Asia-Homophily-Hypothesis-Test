# LastFM Asia – Homophily Hypothesis Test

This project was completed for **Laboratory 3: Hypothesis Testing in Network Analysis**.

The objective is to determine whether an observed network pattern is unusual
relative to an explicitly defined null/reference model.

## Dataset

The analysis uses the **LastFM Asia Social Network** from the Stanford Network
Analysis Project (SNAP).

Dataset source:

https://snap.stanford.edu/data/feather-lastfm-social.html

The network contains:

- **7,624 users**
- **27,806 mutual follower relationships**

A node represents a LastFM user.

An edge represents a mutual follower relationship between two users.

The graph is analyzed as an **undirected and unweighted network**.

The dataset also contains numeric target classes derived from users' country
information.

## Research Question

**Are connected LastFM users more likely to belong to the same country-derived
target class than would be expected under random assignment of the target
labels?**

## Network Mechanism

The mechanism investigated is **homophily**.

Homophily refers to the tendency of similar actors to form relationships more
frequently than dissimilar actors.

## Hypotheses

### H0

The country-derived target labels are unrelated to the observed follower
relationships.

The proportion of same-target edges should be similar to what would be
expected if the existing labels were randomly assigned to users.

### H1

Connected users belong to the same target class more frequently than expected
under random assignment of the target labels.

## Observed Statistic

The statistic used is the proportion of network edges connecting two users
with the same target class.

Observed results:

| Measure | Result |
|---|---:|
| Nodes | 7,624 |
| Edges | 27,806 |
| Same-target edges | 24,299 |
| Same-target proportion | 0.8739 |
| Same-target percentage | 87.39% |

## Null Model

A **label-permutation null model** was used.

The network structure was kept unchanged while the country-derived target
labels were randomly shuffled among users.

The null model preserves:

- all nodes;
- all edges;
- the complete network topology;
- the degree structure;
- the number of users in each target class.

Only the assignment of target labels to individual users was randomized.

This null model is appropriate because the research question concerns whether
target-class similarity is associated with the existing follower relationships.

## Permutation Test

A total of **1,000 permutations** were generated.

For every permutation:

1. the target labels were randomly reassigned to users;
2. the network structure remained unchanged;
3. the proportion of same-target edges was calculated;
4. the resulting statistic was stored in the null distribution.

Results:

| Measure | Result |
|---|---:|
| Observed proportion | 0.8739 |
| Null mean | 0.1193 |
| Null standard deviation | 0.0029 |
| Minimum null value | 0.1107 |
| Maximum null value | 0.1311 |
| Number of permutations | 1,000 |
| Extreme permutations | 0 |
| Corrected p-value | ≈ 0.001 |

## Visualization

The figure below shows the null distribution generated from the 1,000
permutations together with the observed statistic.



The observed same-target proportion is far outside the range produced by the
null model.

## Interpretation

The null hypothesis was rejected.

Users belonging to the same country-derived target class are connected much
more frequently than would be expected if the target labels were randomly
distributed across the network.

The result is consistent with a strong **homophily pattern**.

However, this result should not be interpreted as proof that country similarity
caused users to connect.

Other possible explanations include:

- shared language;
- geographic opportunity;
- local social circles;
- shared musical interests;
- recommendation mechanisms on the platform.

The analysis therefore shows a strong association between target-class
similarity and mutual follower relationships, but it does not establish a
causal mechanism.

## Descriptive Network Results

Several descriptive measures were also calculated to provide context for the
network.

| Measure | Result |
|---|---:|
| Nodes | 7,624 |
| Edges | 27,806 |
| Density | ≈ 0.000957 |
| Transitivity | ≈ 0.1786 |
| Detected communities | 27 |
| Modularity | 0.8127 |

These results show that the network is sparse but has a pronounced community
structure.

## Project Structure

```text
├── Lab3_LastFM_Homophily_Analysis.ipynb
├── README.md
├── requirements.txt
│
├── images/
│   └── lab3_homophily_null_distribution.png
│
├── report/
│   └── Lab3_LastFM_Homophily_Report.pdf
│
└── data/
    ├── lastfm_asia_edges.csv
    ├── lastfm_asia_target.csv
    ├── lastfm_asia_features.json
    └── README.txt