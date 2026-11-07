**# w02_AI_integration
MISSION 1 | Build the AI and ML landscape Research question: What is artificial intelligence, and where exactly does machine learning fit?
 Compare AI, conventional rule-based programming and machine learning.
 Explain the relationship between AI, ML, deep learning, generative AI and LLMs.
 Explain why automation is not necessarily AI, and why AI does not always mean ML.
 Identify what is explicitly programmed versus what can be learned from data.
Deliverable: A labelled concept map, five distinctions written in your own words, and three examples classified with
reasons.
Keep in mind: Do not treat all terms as separate technologies at the same conceptual level.
<img width="1266" height="1011" alt="image" src="https://github.com/user-attachments/assets/b006f20c-da5c-4860-8206-26fbfa5bede4" />**
How to read the map. The terms are not separate technologies at the same level. They nest like this:

AI is the goal: machines doing things that normally need intelligence.
Machine learning is one method for reaching that goal.
Deep learning is one family of ML methods.
Generative AI is one application of deep learning.
LLMs are one kind of generative AI.

Rule-based AI is a second route to the same goal. Automation sits mostly outside the picture and overlaps it only at one point.

Comparing the three approaches
	Conventional programming	Rule-based AI	Machine learning
Who supplies the logic	A programmer	A programmer or domain expert	The training process, from examples
Input to the build	Rules plus data, to get answers	Knowledge plus rules, to get conclusions	Data plus answers, to get rules
Handles messy input	Poorly	Moderately	Well, if the data covered it
Fails when	A case was not anticipated	A case is missing from the knowledge base	The data was biased, thin or out of date
Five distinctions in my own words

1. AI is a goal, ML is a method. “AI” says what a system achieves, such as recognising, planning or conversing. “ML” says how it was built: by adjusting itself on data instead of being told what to do. A goal can be reached by several methods, so the two terms are not interchangeable.

2. Automation is about who does the work; AI is about how decisions get made. A payroll script that runs every Friday replaces human effort, but it makes no judgement. It follows fixed steps, and a programmer could write out every one of them in advance. Automation only becomes AI when the system has to perceive, interpret or adapt, as with a warehouse robot that works out how to grip an unfamiliar object.

3. AI does not always mean ML. Before ML dominated, AI meant systems with expert-written logic, such as medical diagnosis rule sets, route planners and game-tree search. They behave intelligently, yet nothing in them was learned. ML is the dominant way to build AI today, not the only way.

4. The nesting from ML down to LLMs is about technique, not importance. Deep learning is ML that uses many-layered neural networks. Generative AI is a use of those networks to produce new content instead of just labelling inputs. An LLM is a generative model specialised for language. Each term narrows the one above it. Two caveats keep this honest: ML also includes non-deep methods such as decision trees and regression, and not every generative model is a language model (image generators, for example).

5. Explicit versus learned is a split inside one system. Even in an ML system, humans still choose the architecture, the objective (what counts as “good”), the training data and the evaluation. What is learned is the parameters, meaning the numerical weights that encode patterns the programmer never wrote down. Rule-based systems put nearly everything on the explicit side. LLMs put almost all the detailed behaviour on the learned side, which is also why they are harder to inspect and why they can fail in unexpected ways.

Three examples classified

Example 1: A bank’s scheduled script that flags any transaction over a fixed amount.

Automation: yes. Conventional programming: yes. AI: no. ML: no.
Reason: a threshold and a schedule are fully specified in advance. The system does not interpret anything or adapt to anything.

Example 2: A chess engine that searches possible moves and scores positions using formulas its designers wrote.

AI: yes. Rule-based or symbolic AI: yes. ML: no.
Reason: playing strong chess takes planning and evaluation, which counts as intelligent behaviour. But every evaluation rule was handwritten, so nothing was learned from data. This is the clearest case of AI without ML.

Example 3: A chat assistant that drafts and answers questions in natural language.

AI, ML, deep learning, generative AI and LLM: all yes, at once.
Reason: it is trained on huge text collections (ML) using a many-layered neural network (deep learning), and it produces new text instead of choosing a label (generative AI). It specialises in language (LLM). The explicit parts are the architecture, training objective and safeguards. The learned part is the billions of weights that hold its language patterns.

The thing to remember is that the same product can carry several labels, because the terms describe different layers. The AI/ML/DL/GenAI/LLM chain describes how it was built, while “automation” describes whether people were removed from the task. Automation can also exist with none of the others.
_____________________________________________________________________________________________________________________________

**MISSION 2 | Understand data: what does an ML system learn from?
Research question: What does it mean to learn a pattern from data?
 Investigate dataset, sample, observation, feature, label and target.
 Distinguish structured and unstructured data, and numerical and categorical features.
 Distinguish labelled and unlabelled examples.
 Research data collection, cleaning, missing values, noisy data and inconsistent labels.
 Explain why data quantity alone does not guarantee data quality.
Deliverable: Create a small illustrative dataset with at least six rows. Identify its features and, where applicable, its
target. Explain two ways data quality could affect a model.
Keep in mind: Use synthetic or public data only. A chip-design example could use historical measurements to predict a
timing pass/fail outcome.**

# Mission 2: What does an ML system learn from?

## What does it mean to "learn a pattern from data"?

An ML model adjusts its internal parameters so that its outputs match the relationships found in many past examples. In effect, it finds a rule that connects inputs to outcomes, then applies that rule to new cases. A "pattern" is a statistical regularity, such as "when logic depth is high and the clock period is short, timing usually fails". The model does not understand the physics. It only knows what the examples show it, so the data defines the ceiling of what it can learn.

## Key vocabulary

| Term | Meaning | Chip-design example |
|---|---|---|
| **Dataset** | The whole collection of examples | All timing-path records from past projects |
| **Sample / observation / row** | One example | One timing path under one corner |
| **Feature** | An input property the model uses | Clock period, logic depth |
| **Label** | The known correct answer attached to an example | PASS or FAIL from sign-off analysis |
| **Target** | The quantity the model is trained to predict. The labels are its recorded values. | `timing_met` |

"Label" and "target" are often used interchangeably. Strictly, the target is the variable you want to predict, and the labels are its observed values in your data.

**Structured vs unstructured data.** Structured data fits rows and columns with defined fields (spreadsheets, databases, measurement logs). Unstructured data has no fixed schema, such as images, free text, audio, or raw layout files. Unstructured data usually needs to be converted into features first.

**Numerical vs categorical features.** Numerical features are measurable quantities (clock period in ns, wire length in µm). Categorical features are group names (corner = SS/TT/FF, block type = ALU/FPU). Categories usually need encoding before a model can use them.

**Labelled vs unlabelled.** A labelled example includes the answer (features plus PASS/FAIL). An unlabelled example has features only. Labelled data supports supervised learning (predicting a target). Unlabelled data supports finding structure, such as clustering similar paths.

## Data collection and quality problems

**Collection** means gathering data from simulations, tools, sensors, logs, or public sources. How it is collected determines what it represents. Data from only one project or one process node will describe only that world.

**Cleaning** means fixing or removing problems before training. The main ones are:

- **Missing values:** a field is empty (a failed extraction, a tool that didn't report). You can remove the row, fill the gap with a reasonable estimate, or flag it as missing. Careless filling can invent patterns that aren't real.
- **Noisy data:** values contain random error or mistakes, such as measurement jitter, unit mix-ups (µm vs nm), or typos.
- **Inconsistent labels:** the same or near-identical inputs carry different labels. Causes include different pass/fail thresholds between teams, human error, or labels from different tool versions.

**Why quantity does not guarantee quality.** A million rows can still be wrong, duplicated, biased, or unrepresentative. If 99% of the rows come from easy, passing designs, the model can score 99% accuracy by always predicting PASS while being useless at spotting failures. More data only helps if it is accurate, consistent, relevant, and covers the situations the model will face. Large volumes of bad data can also make a model confidently wrong, because the flaws look like patterns.

## Deliverable: a small synthetic dataset

This is synthetic data I made up for illustration, based on predicting whether a timing path meets timing.

| path_id | clock_period_ns | logic_depth | wire_length_um | corner | block_type | timing_met |
|---|---|---|---|---|---|---|
| P01 | 1.0 | 12 | 450 | SS | ALU | FAIL |
| P02 | 1.0 | 12 | 450 | TT | ALU | PASS |
| P03 | 1.2 | 15 | 600 | SS | FPU | FAIL |
| P04 | 1.5 | 15 | 600 | SS | FPU | PASS |
| P05 | 1.5 | 9 | 300 | TT | Decoder | PASS |
| P06 | 0.8 | 14 | **5200** | FF | ALU | PASS |
| P07 | 0.8 | 18 | **(missing)** | SS | FPU | FAIL |
| P08 | 1.2 | 15 | 600 | SS | FPU | **PASS** |

**Identification**

- **Observations:** 8 rows, each one timing path.
- **Identifier (not a feature):** `path_id`. It labels the row but carries no predictive meaning.
- **Numerical features:** `clock_period_ns`, `logic_depth`, `wire_length_um`.
- **Categorical features:** `corner`, `block_type`.
- **Target:** `timing_met` (PASS/FAIL), a binary categorical target, so this is a classification task. All 8 rows are labelled. If a new path arrived without a result, it would be an unlabelled example for the model to predict.
- **Structure:** structured, tabular data.

**Deliberate flaws:** P06 has a likely unit typo (5200 instead of 520), P07 has a missing wire length, and P03 and P08 have identical features but opposite labels.

## Two ways data quality could affect a model

**1. Inconsistent labels (P03 vs P08) limit what the model can learn.** The model sees identical inputs with contradictory answers, so no rule can fit both. It may either settle on a middle ground that is right only half the time for such paths, or contort itself (overfit) to memorise the contradiction using irrelevant details. Either way, accuracy and confidence scores become unreliable. The fix is to find out why the labels differ, such as different sign-off thresholds or a tool version change, and agree on one definition of PASS.

**2. Noisy and missing feature values (P06, P07) distort the learned relationship.** A wire length of 5200 µm, about ten times larger than its neighbours, paired with a PASS, could teach the model that very long wires are fine. That would be the opposite of the real physical trend. The model could then predict PASS for genuinely risky long routes. The missing value in P07 forces a choice: dropping the row loses one of the few FAIL examples, and filling it with an average could hide that this path was probably long and slow. Cleaning here means checking units, flagging outliers, and handling missing data deliberately rather than silently.

A third risk is worth noting: this dataset has only 8 rows and little coverage of the FF corner, so even after cleaning it would not represent real designs. Quantity and coverage matter too, but only alongside quality.

_____________________________________________________________________________________________________________________________

**MISSION 3 | Understand the main ML approaches
Research question: How does a system learn when it has labels, no labels, or feedback from actions?
 Compare supervised learning, unsupervised learning and reinforcement learning.
 Describe the training signal each approach uses, what it produces and one limitation.
 Recognise self-supervised learning as a related approach in which targets are derived from the data itself.
 Explain why self-supervised learning is not simply another name for unsupervised learning in every context.
Deliverable: A comparison table, one simple diagram of each learning process, and a short explanation of when
each approach may be suitable.
Keep in mind: Keep self-supervised learning introductory; its deeper connection to neural networks and LLMs comes
later.**

<img width="1226" height="315" alt="image" src="https://github.com/user-attachments/assets/85b2e602-9664-4399-85d7-0b49ab96f46d" />

## When each approach may be suitable

- **Supervised:** use it when you have a clear question and enough trustworthy labelled examples, such as predicting timing pass/fail from past sign-off results. It is the most direct choice when the answer is known for historical data.
- **Unsupervised:** use it when you want to explore data or find structure but have no labels, such as grouping paths by behaviour or spotting unusual measurements. It suits discovery more than prediction.
- **Reinforcement:** use it when a system must make a sequence of decisions, can safely try many actions (usually in a simulator), and a numeric reward can be defined. Floorplanning and placement tuning are typical candidates. It is a poor fit when trials are expensive or the reward is hard to define.

## Self-supervised learning (introduction)

In self-supervised learning, the system creates its own targets from the data. For example, hide one field in a record, or one word in a sentence, and train the model to predict the hidden part from the rest. The answer is already inside the data, so no human has to label anything.

It is not simply another name for unsupervised learning for two reasons:

1. **It has a target and a loss.** Unsupervised methods such as clustering have no target to predict. Self-supervised training works like supervised training: predict, compare with a target, and correct the error. The target just comes from the data rather than from human annotators.
2. **The goal differs.** Unsupervised learning usually aims to describe the data's structure. Self-supervised learning usually aims to produce a model that can be reused for other tasks later.

It is easy to see why the terms get mixed up. Both avoid human-written labels, and some textbooks and papers file self-supervised learning under "unsupervised". The classification depends on context, so it helps to ask whether the training has a target, even a self-made one. The deeper links to neural networks and LLMs can wait for later missions.
_____________________________________________________________________________________________________________________________

**MISSION 4 | Understand ML task types
Research question: What kinds of problems can machine learning solve?
 Distinguish classification, regression, clustering, anomaly detection, dimensionality reduction, and
recommendation/ranking.
 For every task, identify likely input data and the expected output.
 Explain why task type is different from learning paradigm.
 Recognise that multiple algorithms or approaches may address a similar task.
Deliverable: Classify at least six real-world problems by task type. State the input and output for each, including at
least two semiconductor-related examples.
Keep in mind: A task type does not, by itself, tell you how a model was trained.**

# Mission 4: What kinds of problems can ML solve?

A task type describes the shape of the problem: what goes in and what kind of answer comes out. It says nothing about how the model is trained, which is the learning paradigm from Mission 3.

## The six task types

| Task | Question it answers | Typical input | Expected output |
|---|---|---|---|
| **Classification** | Which category does this belong to? | Features of one example | A discrete class (or class probabilities) |
| **Regression** | How much, or what value? | Features of one example | A continuous number |
| **Clustering** | Which examples are alike? | Many examples, no categories given | A group assignment for each example |
| **Anomaly detection** | Is this unusual compared with normal? | Features of one example, often mostly normal history | An anomaly score or a normal/abnormal flag |
| **Dimensionality reduction** | Can I describe this with fewer features? | Examples with many features | A smaller set of new features (for example 2 or 3 coordinates) |
| **Recommendation / ranking** | What should come first for this user or query? | User, query and item information, plus past interactions | An ordered list of items or scores |

## Real-world problems classified

| # | Problem | Task type | Input | Output |
|---|---|---|---|---|
| 1 | Email spam filter | Classification | Email text, sender, links, metadata | Spam or not spam |
| 2 | House price estimate | Regression | Floor area, location, rooms, age | A price (number) |
| 3 | Customer segmentation for a shop | Clustering | Purchase history and visit frequency per customer | A segment ID for each customer |
| 4 | Credit card fraud alert | Anomaly detection | Transaction amount, place, time, merchant, past behaviour | Fraud-suspicion score or flag |
| 5 | Visualising thousands of gene measurements per patient | Dimensionality reduction | Thousands of measurements per sample | 2 or 3 summary coordinates per sample |
| 6 | Video streaming "recommended for you" | Recommendation / ranking | Viewing history, ratings, video details | A ranked list of videos |
| 7 | **Semiconductor:** timing pass/fail for a path (the Mission 2 dataset) | Classification | Clock period, logic depth, wire length, corner, block type | PASS or FAIL |
| 8 | **Semiconductor:** predicting a chip's maximum operating frequency from test measurements | Regression | Process-monitor readings and parametric test values per die | Predicted frequency (a number, e.g. in GHz) |
| 9 | **Semiconductor:** spotting abnormal behaviour in a fab tool | Anomaly detection | Time series of sensor readings (temperature, pressure, gas flow) | Anomaly score or alert for a process run |

Other semiconductor tasks follow the same patterns. Sorting wafer-map images into defect types is classification. Grouping similar failing dies is clustering.

## Why task type is different from learning paradigm

The task is the question you want answered. The paradigm is how the learner gets its training signal. They are separate choices, and one task can be approached with different paradigms:

- **Anomaly detection** can be supervised if you have labelled faults. It can be unsupervised if you only have normal data and flag whatever looks different. A mix of the two is also common.
- **Dimensionality reduction** is often unsupervised (PCA). An autoencoder doing the same job is trained by predicting its own input, which is self-supervised.
- **Recommendation** can be supervised (predict a rating), unsupervised (find similar users or items), or reinforcement-style (learn from which suggestions people actually click).
- **Classification** is most often supervised, but a classifier can start from self-supervised pretraining. Clustering, though, is usually unsupervised.

A task type does not tell you how the model was trained. Hearing "this is a classifier" tells you the output is a category, and nothing about whether it learned from human labels, self-made targets, or feedback.

## Multiple approaches can address one task

Many algorithms can address the same task, and each has its own strengths:

- **Classification:** logistic regression, decision trees, random forests, gradient boosting, neural networks.
- **Regression:** linear regression, gradient boosting, neural networks.
- **Clustering:** k-means, hierarchical clustering, DBSCAN.
- **Anomaly detection:** statistical thresholds, isolation forests, autoencoder reconstruction error.
- **Dimensionality reduction:** PCA, t-SNE, UMAP, autoencoders.
- **Ranking:** learning-to-rank models, collaborative filtering.

The same real problem can also be framed as different tasks. Timing could be classification (will this path pass?) or regression (how many picoseconds of slack will it have?). The regression answer carries more detail, but it needs numeric slack values rather than a simple PASS/FAIL label. Choosing the framing is part of the design work, and it depends on what decision the output will support and what data you actually have.
____________________________________________________________________________________________________________________________

**MISSION 5 | Understand the anatomy of an ML model
Research question: What happens between feeding data into an ML system and receiving a prediction?
 Distinguish an algorithm, a model and learned parameters.
 Explain training versus inference.
 Describe how model outputs can be compared against target answers during training.
 Explain the intuition behind loss/error measures and optimisation.
 Understand linear regression conceptually: learning a relationship from example inputs and numerical outcomes
to estimate an outcome for a new input.
Deliverable: A labelled flow diagram from examples through training to a trained model and inference result, plus a
short explanation of linear regression.
Keep in mind: Introduce parameters, loss and optimisation without requiring calculus or detailed equations. Different ML
methods learn in different ways.
**
Here is the flow from examples through training to a trained model and an inference result.

## Reading the diagram

**Algorithm, model, parameters.** These three are easy to mix up:
- The algorithm is the learning recipe, for example "fit a straight line to the data." It is chosen by people before training.
- The model is what the algorithm produces: a rule that turns inputs into outputs.
- The parameters are the adjustable numbers inside the model. They are the only part that changes during learning. "Learned parameters" are the values they settle on.

A useful analogy is a recipe (algorithm), a finished dish (model) and the exact amounts of salt and spice you settled on (parameters).

**Training vs inference.** Training is the left-hand loop in Phase 1. The model sees examples where the correct answer is known, and its parameters are changed to improve. Inference is Phase 2. The finished model gets a new input with no known answer and produces a prediction, and the parameters no longer change.

**Comparing outputs with targets.** During training the model makes a guess for each example input. That guess is compared with the target answer that came with the example, and the gap is the error.

**Loss and optimisation, intuitively.** The loss turns many errors into a single score, where lower is better. A common choice is to square each error, so big misses count much more than small ones, and then average them. Optimisation is the process of changing the parameters so that the loss goes down. You can think of it as tuning a radio by hand: turn the dial a little, check whether the signal is clearer, and keep going in the direction that helps. The optimiser repeats this many times, and training stops when the loss no longer improves much.

## Linear regression in brief

Linear regression learns a relationship between inputs and a numerical outcome from examples. Suppose you have records of house sizes and sale prices. Plotted as points, they roughly rise together. The model is a straight line through those points, and its two parameters are where the line starts (its base level) and how steeply it rises (how much the price goes up per extra square metre).

At the start, the line is a poor guess. The loss measures how far the points sit from it, and the optimiser tilts and shifts the line until the overall distance is as small as it can be. That best-fitting line is the trained model. At inference you give it a new house's size, find that size on the line, and read off the estimated price.

It is "linear" because the model assumes a steady, proportional relationship. That makes it simple and easy to interpret, but it will fit poorly if the real pattern is curved or more complex.

Different ML methods learn in different ways. Linear regression adjusts just a few parameters. A neural network adjusts millions, and a decision tree learns by choosing where to split the data rather than by tuning numbers. All of them still follow the same pattern: examples, a measure of error, and a way of improving.
