Project Proposal: Causal Discovery and Inference for Early Online Engagement and Course Completion in the Open University Learning Analytics Dataset

Shreyash Kondakindi
A69034537
skondakindi@ucsd.edu
Aayush Salvi
A69044350
avsalvi@ucsd.edu
Jai Srivastav
A69043969
jsrivastav@ucsd.edu
Atharva Hirulkar
A69044077
ahirulkar@ucsd.edu

Abstract
We propose a course project on the causal effect of early online engagement on end-
of-course success in the Open University Learning Analytics Dataset (OULAD).
Our goal is to combine a domain-informed causal graph, a small-scale causal
discovery analysis, and observational effect estimation on a public dataset that is
feasible to analyze on a standard laptop. We focus on a concrete question: whether
higher engagement during the first two weeks of a course presentation improves the
probability of successful completion after adjustment for plausible pre-treatment
confounders. This proposal is designed to be realistic within the course timeline
and to produce an interpretable final report and presentation.

1 Project description
We propose to study whether early online engagement causally affects course completion in OULAD
[6]. OULAD is a public learning analytics dataset released by the Open University. It links stu-
dent background variables, registration records, assessment information, and daily virtual learning
environment activity for more than 32,000 students across multiple module presentations [6]. The
dataset is well suited for the course because it supports both causal discovery and causal inference
using observational data, and it does not require IRB approval, proprietary access, or expensive
computation.
Our main question is straightforward: among otherwise similar students, what is the effect of higher
early engagement on the probability of successful course completion? We plan to define treatment
using cumulative virtual learning environment activity in the first 14 days of a module presentation,
normalized within each module-presentation to account for differences in course structure. Our
primary outcome will be successful completion, defined as pass or distinction versus fail or withdrawal
after checking the raw outcome labels during data preparation. We will also consider withdrawal as a
secondary outcome because it is substantively meaningful and easier to interpret for student support.
This topic is a strong fit for the course for two reasons. First, it is genuinely causal rather than
purely predictive. Much of the existing OULAD literature focuses on student risk prediction or
performance prediction [5]. Our project instead asks an intervention-style question. Second, the
project naturally connects a hand-built DAG, causal discovery methods from class, and standard
observational adjustment methods. That combination makes the project methodologically aligned
with the course while keeping the empirical scope narrow enough to finish well.

2 Initial ideas on how we will tackle the problem
2.1 Research question and causal target
Our main estimand is the average treatment effect of a binary treatment comparing high versus
low early engagement. Rather than assessing whether engagement merely predicts success, we
evaluate whether students with similar observed pre-treatment characteristics would experience
different completion outcomes under varying engagement levels. This distinction is important
because factors such as prior education, disability status, study load, and previous attempts may affect
both engagement and completion [9, 3]. We address one primary and a few secondary questions:
the causal effect of high early engagement on course completion; whether this effect varies by prior
education or past attempts; whether findings remain consistent across module presentations; and
whether causal discovery results broadly support the adjustment assumptions in our hand-crafted
DAG.
2.2 Data and variable construction
We will construct a student-level dataset by integrating OULAD files on demographics, outcomes,
registration, daily virtual learning environment activity, assessments, and results [6]. Because
module presentations differ especially B and J types, we will normalize engagement within each
presentation and include robustness checks [7]. The treatment is high early engagement in the first 14
days. Covariates include pre-treatment variables such as demographics, prior attempts, credits, and
registration details, while later performance and activity are treated as post-treatment and excluded
from adjustment.
2.3 Causal framework
Before modeling, we will specify a domain-informed DAG where student background and module
design influence both early engagement and outcomes. Early engagement is expected to affect
completion partly via downstream variables (e.g., later assessments and activity), treated as mediators,
not confounders. Identification relies on consistency, positivity, and conditional exchangeability
given pre-treatment covariates [3, 4]. A key concern is unobserved motivation or time constraints, so
sensitivity analyses and robustness checks will be integral to the design.
2.4 Planned methods
• Hand-built DAG and adjustment set: We first construct a domain-informed DAG and identify a
primary adjustment set using causal inference principles [8, 9], clearly separating pre-, post-, and
ambiguous variables.
• Reduced causal discovery analysis: We apply PC/FCI (constraint-based) and GES (score-based)
on a reduced variable set to test assumptions [10, 1], compare outputs with the DAG, and note
agreements, conflicts, and unstable edges (FCI helps address latent confounding).
• Observational effect estimation: We estimate effects using IPTW and AIPW [3, 2], plus a
baseline method, reporting balance, overlap, and sensitivity analyses.
2.5 Feasibility, risks, and fallback plan
The project is feasible as the data are public, well-documented, and can be handled in Python using
standard tools, with most effort in data construction, treatment definition, and balance checks. Key
risks include unmeasured motivation, limited comparability across module presentations, and unstable
discovery results with mixed variables. We address these via a small variable set, normalization
within presentations, multiple treatment windows (7/14/21 days), and pooled vs stratified analyses. A
fallback retains a hand-built DAG, one discovery method, and a single robust causal effect estimate
with sensitivity checks.
2.6 Expected deliverables
By the final report, we expect to produce the following: a cleaned student-level analysis dataset,
descriptive summaries of treatment and outcome prevalence, a hand-built DAG figure, at least one
causal discovery graph on a reduced variable set, treatment effect estimates from weighting and
doubly robust estimation, balance and overlap diagnostics, a short robustness section, and a final
presentation that clearly distinguishes causal claims from predictive claims. This scope is ambitious
but manageable, and it gives us a clear path from proposal to implementation.

References
[1] David M. Chickering. Optimal structure identification with greedy search. Journal of Machine
Learning Research, 3:507–554, 2002.
[2] Adam N. Glynn and Kevin M. Quinn. An introduction to the augmented inverse propensity
weighted estimator. Political Analysis, 18(1):36–56, 2010.
[3] Miguel A. Hernán and James M. Robins. Causal Inference: What If. Chapman & Hall/CRC,
2020.
[4] Guido W. Imbens and Donald B. Rubin. Causal Inference for Statistics, Social, and Biomedical
Sciences. Cambridge University Press, 2015.
[5] Linqi Jin, Yuning Wang, Hayeon Song, and Hyo-Jeong So. Predictive modelling with the Open
University Learning Analytics Dataset (OULAD): A systematic literature review. In Artificial
Intelligence in Education, pages 477–484. Springer, 2024.
[6] Jakub Kuzilek, Martin Hlosta, and Zdenek Zdrahal. Open University Learning Analytics dataset.
Scientific Data, 4:170171, 2017.
[7] Open University Knowledge Media Institute. Open University Learning Analytics Dataset
documentation. https://analyse.kmi.open.ac.uk/open-dataset, accessed April 2026.
[8] Judea Pearl. Causality: Models, Reasoning, and Inference. Cambridge University Press, second
edition, 2009.
[9] Judea Pearl, Madelyn Glymour, and Nicholas P. Jewell. Causal Inference in Statistics: A Primer.
Wiley, 2016.
[10] Peter Spirtes and Kun Zhang. Causal discovery and inference: Concepts and recent method-
ological advances. Applied Informatics, 3(3), 2016.