# w02_AI_integration
MISSION 1 | Build the AI and ML landscape Research question: What is artificial intelligence, and where exactly does machine learning fit?
 Compare AI, conventional rule-based programming and machine learning.
 Explain the relationship between AI, ML, deep learning, generative AI and LLMs.
 Explain why automation is not necessarily AI, and why AI does not always mean ML.
 Identify what is explicitly programmed versus what can be learned from data.
Deliverable: A labelled concept map, five distinctions written in your own words, and three examples classified with
reasons.
Keep in mind: Do not treat all terms as separate technologies at the same conceptual level.
<img width="1266" height="1011" alt="image" src="https://github.com/user-attachments/assets/b006f20c-da5c-4860-8206-26fbfa5bede4" />
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
