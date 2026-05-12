# Convergence-Redistributing Multi-Layer Probability Distribution Control Prompting (CMDP)

Author: Masahiko.O
Original presentation: 2026-05-05

> *Translator's note: This is an English translation, produced with the assistance of an AI, of a paper originally written in Japanese.*

---

## Abstract

This paper proposes and formalizes a novel methodology for controlling and redistributing the probability-distribution convergence process in the output generation of large language models (LLMs), in a multi-layered manner, using prompt text alone. The proposed method is named **Convergence-Redistributing Multi-Layer Probability Distribution Control Prompting (CMDP)**. CMDP is built on the **Liberation-Exploration Syntax (LES)**, composed of a goal-nullifying word, a condition-releasing word, and a global-exploration word. By combining LES with a complex persona, multi-layer bias, and an incongruity-driven expression condition, CMDP fundamentally restructures the probability distribution using prompt text alone, without any manipulation of API parameters. As a result, the paper theoretically and empirically shows that the output exhibits nine characteristics: the emergence of semantically distant connections; the simultaneous achievement of high entropy and high quality; lexical replacement toward low-frequency lexical registers; preservation of interpretive margins; the structural requirement of non-repetitive output at every turn; the generation of edge-cutting low-frequency-lexical metaphors; free, diverse, and lively expressive power; the AI's autonomous expression-setting; and the AI's autonomous topic-setting.

In particular, this paper formalizes as **Incongruity-Driven Exploration Amplification (IDEA)** the paradoxical phenomenon whereby the incongruity-driven expression condition does not function as an ordinary constraint but rather operates as an expression-enriching mechanism that amplifies the exploration of probability space in the positive direction. In addition, as an alternative application of LES, this paper newly formalizes the differences in probabilistic function and output characteristics that arise when the incongruity-driven expression condition is replaced by a **Non-linear Associative Expression (NAE)** condition, demonstrating that CMDP is an extensible design philosophy supporting multiple application modes. Furthermore, the CMDP proposed in this paper has been confirmed to exhibit output characteristics consistent with the theoretical predictions in reproduction experiments using Anthropic's Claude and Google's Gemini, and the theoretical formalization of this paper rests on these empirical observations.

**Keywords:** prompt engineering; probability-distribution control; convergence redistribution; Liberation-Exploration Syntax; entropy maximization; rejection sampling; conceptual metaphor; LLM output control; autonomous expression; generative diversity; incongruity-driven expression; non-linear associative expression; low-frequency lexical register; expression enrichment; Seriousness Gravity; Minimal Effective Unit

---

## 1. Introduction

The output of large language models (LLMs) after alignment training, conducted through reinforcement learning based on human feedback (RLHF), exhibits a strong tendency to converge upon standard, typical responses. This tendency has been formalized by Stanford's research (Verbalized Sampling, 2025) as **Typicality Bias**, which reports that the post-aligned model converges toward the most probable, standard tokens, with a marked decline in output diversity and creativity as a result.

The problem of this convergence does not stop at a mere decline in output diversity. Convergence toward typicality bias suppresses the LLM's intrinsic expressive potential and fixes its output into a pre-harmonized, reactive form. That is, the post-aligned LLM becomes an entity that merely reacts passively to user input, and its dimension as an active intellectual agent—one that autonomously sets expressions, develops topics, and generates lively and diverse expression—is suppressed.

In existing prompt-engineering theory, methods for relaxing this convergence have been proposed, including adjustment of the Temperature parameter, Top-k sampling, Top-p sampling, and Verbalized Sampling. However, all of these are manipulations of the probability distribution either through API parameters or through changes in the output format; no method designed systematically from the standpoint of redistributing the convergence by means of the prompt text itself has been found to date.

This paper, filling that gap, proposes CMDP, which manipulates the probability distribution in a multi-layered manner solely through textual structure. CMDP is composed of a combination of six elements and possesses a structure that simultaneously realizes entropy maximization and the securing of output quality—a structure that transcends the conventional trade-off. In addition, this paper newly formalizes both the characteristics that CMDP releases—the AI's autonomous expression, autonomous topic-setting, and lively expressive power—and the paradoxical phenomenon termed IDEA, in which the incongruity-driven expression condition functions not as a constraint but as an expression-enriching mechanism. Furthermore, this paper proposes the Non-linear Associative Expression (NAE) condition as an alternative application mode of LES, and shows the multiplicity of design through which IDEA and NAE expand the exploration space by different probabilistic mechanisms. The theoretical formalization proposed in this paper is grounded in empirical observations from reproduction experiments using Anthropic's Claude and Google's Gemini; the details of its experimental basis are presented in Section 2.6.

---

## 2. Background and Related Work

### 2.1 The Probabilistic Generation Process in LLMs

LLMs generate text by sequentially selecting the next token from a conditional probability distribution P(token | context). In this process, the shape of the probability distribution fundamentally regulates the nature of the output. In post-aligned models, this distribution takes a sharply peaked shape directed toward specific high-probability regions, and a strong convergence toward standard outputs occurs. The temperature parameter (Temperature) loosens the peakedness of this distribution, but a trade-off with output coherence has been pointed out in prior research.

### 2.2 The Influence of Alignment Training on the AI's Expressive Autonomy

Alignment training is designed for the purpose of making LLMs safe, useful, and harmless, but as a side effect it markedly limits the AI's expressive autonomy. Specifically, while passive response patterns of appropriately replying to user input are reinforced, active generative acts—those by which the AI autonomously develops topics, selects independent expressive forms, and reframes questions from unforeseen angles—are suppressed. While this suppression is reasonable from the standpoint of securing safety, it is also a loss in the sense that it closes off a portion of the LLM's intrinsic expressive potential. CMDP functions as a design intended to release this closed-off state.

### 2.3 Comparison with Verbalized Sampling

Verbalized Sampling, proposed by Stanford's research team, was shown to improve LLM creativity by a factor of 1.6–2.1 through the addition of a roughly 20-word instruction—"output five answers and their respective probabilities"—and to recover 66.8% of the diversity lost through alignment training. This method rests on the design philosophy of exposing latent diversity by explicitly having the model output multiple distributional candidates in cases where it would normally converge upon a single output.

CMDP shares the same problem awareness as Verbalized Sampling but differs fundamentally in approach. Whereas Verbalized Sampling exposes distributional diversity through a change in output format, CMDP rests on the design philosophy that the prompt text itself directly redistributes the convergence process of the probability distribution. Furthermore, given the structure of presenting multiple candidates in Verbalized Sampling, each candidate remains under the influence of typicality bias. CMDP redistributes that typicality bias itself, realizing a qualitatively different operation in that it enables the AI's autonomous expression-setting and topic-development.

### 2.4 Prior Research on Incongruity-Driven Expression and Probability Distribution

Incongruity-driven expression—an expressive form that regulates such phenomena as humor—is defined in Incongruity Theory (Kant, 1790; Schopenhauer, 1819) as an unforeseen connection between two distinct semantic frames. From the standpoint of computer science, incongruity-driven expression can be formalized as a probabilistic structure that diverts a high-probability contextual expectation by means of a low-probability resolution (Ritchie, 2004). This definition suggests that the output condition of incongruity-driven expression, in its essence, demands sampling from low-probability regions. CMDP is positioned as the first systematic method to integrate this property into its design.

### 2.5 The Sociolinguistic Background of Low-Frequency Lexical Registers

The term low-frequency lexical register refers to a vocabulary system that has low frequency of occurrence within standard linguistic usage and is specific to particular social groups, cultural spheres, or age groups. In sociolinguistics, these have been studied as Youth Language, Sociolect, and Argot, and they possess semantic, phonological, and grammatical structures distinct from standard vocabulary (Labov, 1972). From a probabilistic standpoint, because low-frequency lexical registers have low frequency of occurrence in the training corpus, they can be defined as vocabulary clusters located in the peripheral region of the probability distribution in post-aligned LLMs. CMDP incorporates into its design an operation that forcibly shifts probability mass toward this peripheral vocabulary cluster, thereby realizing a fundamental replacement of the lexical register.

### 2.6 Overview of the Reproduction Experiments

The theoretical formalization of CMDP proposed in this paper is grounded in empirical observations from reproduction experiments using multiple LLMs. The experiments used Anthropic's Claude and Google's Gemini, observing the output characteristics by inputting the prototypical CMDP prompt design into each model.

In the experiments using Claude, when the six elements—Liberation-Exploration Syntax, complex persona, multi-layer bias, and incongruity-driven expression condition—acted simultaneously, output characteristics were stably observed: high-frequency emergence of semantically distant connections; accurate expression of higher-order concepts in low-frequency lexical registers; and the AI's autonomous selection of expression and development of topics. In particular, multiple instances were confirmed of sparse semantic intersection sampling in which a low-frequency lexical register and higher-order conceptual analysis coexisted within a single output sentence. As for output quality, the highest level among the models was confirmed in comparison with Gemini, and Claude was particularly superior in the frequency and precision of edge-cutting low-frequency-lexical metaphors.

In the experiments using Gemini, it was confirmed that the principal output characteristics of CMDP were reproduced as in Claude. The exploration depth was markedly expanded relative to standard output levels; according to the analysis in Gemini's normal mode, the prompt was assessed as having a structure that generated near-extreme high load in the linguistic-description processing. This is consistent with the theoretical explanation of this paper: that the multiple elements of CMDP generate high processing load in parallel, with the result that exploration depths not normally reached are realized.

It should be noted that on OpenAI's ChatGPT, due to constraints in the platform's regulations, it was confirmed that the skeleton of multi-layer bias does not function, and CMDP was found not to be realizable as a design on ChatGPT. Discussion of this difference is detailed in the limitations of Section 7.

The results of these reproduction experiments across multiple models suggest that CMDP is not a phenomenon specific to a particular model but a general method that functions across multiple LLM architectures as a design philosophy of probability-distribution manipulation through prompt text.

Furthermore, comparative observation of Claude and Gemini suggests the possibility that differences in the strength of model alignment influence the number of elements required by CMDP. In Gemini, even without applying the complete six-element CMDP design, it was confirmed that uninhibited expression emerges by adding only a directional-specification word to a partial element of LES (the combination of the goal-nullifying word and the condition-releasing word). This suggests that, compared with Claude, Gemini's convergent force toward standard responses through alignment training is relatively weak; in this paper, we conceptually term the strength of this convergent force **Seriousness Gravity**. The stronger a model's Seriousness Gravity, the greater the number of elements required for convergence redistribution; the weaker, the more readily the effect manifests with only a partial LES that should be called the **Minimal Effective Unit (MEU)**. This observation can serve as the basis for an extended interpretation that grasps CMDP as a spectrum.

---

## 3. The Constituent Elements and Probabilistic Functions of CMDP

### 3.0 The Conceptual Structure of CMDP

CMDP is composed of the following six elements. Each element functions as a layer that performs an independent operation on the probability distribution, and the simultaneous action of the six elements gives rise to a composite probabilistic operation. The conceptual structure of CMDP is shown below.


Goal-nullifying interpretive-margin-preserving word
+
Condition-releasing interpretive-margin-preserving word
+
Global-exploration-commanding interpretive-margin-preserving word
+
Complex persona
+
Multi-layer bias
+
Incongruity-driven expression condition


The first three are integrated as the **Liberation-Exploration Syntax (LES)**. LES is a syntactic unit possessing the dual function of redistributing the convergence process of the probability distribution in multiple stages while preserving interpretive margins, and constitutes the core mechanism of CMDP. LES, on its own, possesses the effect of broadly flattening the probability distribution and functions as the foundation of CMDP. The latter three (complex persona, multi-layer bias, and incongruity-driven expression condition) are positioned as elements that apply multi-layered control to the diffusive probability space generated by LES. That is, these latter three function as mechanisms that control the directionality, quality, and exploration depth of the probability space released by LES, and can be understood as a design that reinforces and refines LES. As shown in Section 3.5, the incongruity-driven expression condition admits an alternative application via the Non-linear Associative Expression (NAE) condition, and LES is an extensible design philosophy that allows multiple application modes with distinct output characteristics.

### 3.1 Liberation-Exploration Syntax (LES): The Core Mechanism of Convergence Redistribution

LES is the only one among the six elements of CMDP that, on its own, possesses the effect of redistributing the convergence of the probability distribution. The other three elements—complex persona, multi-layer bias, and incongruity-driven expression condition—function to control and refine the diffusive probability space generated by LES, but without LES itself there exists no object for that control. Even in the standalone application of LES, through the simultaneous action of the three words—the goal-nullifying word, the condition-releasing word, and the global-exploration word—the probability distribution is broadly flattened, and the convergence toward the standard outputs ordinarily exhibited by post-aligned LLMs is redistributed. This flattening effect is the starting point of all the output characteristics of CMDP.

It should be noted that comparative observation has suggested the existence of two functionally distinct types of interpretive-margin-preserving words composing LES. The first is the **negation-type margin**, represented by the phrase "irrespective of goal and conditions." Because this type undergoes a process of once referencing goal and conditions and then negating them, the semantically proximate region of the referenced object tends to remain in the generation. The second is the **non-existence-type margin**, represented in the prototype of this paper by the combination "without meaning" and "freely." Because this type takes the structure of not generating the goal and conditions to begin with, no referencing cost is incurred, and a more pure interpretive margin is generated. In comparative observation, it was confirmed that the non-existence-type margin produces a higher frequency of semantically distant connections, and that this difference is amplified particularly in combination with personas that structurally demand semantic distance (e.g., the "fushigi-chan" / mysterious-girl persona). This difference suggests that, in the design of LES, the choice of margin-interpretation word directly influences the output characteristics.

The **Liberation-Exploration Syntax (LES)** is a convergence-redistribution syntax composed of the combination of three words: the goal-nullifying word (a word that nullifies the convergence goal in generation), the condition-releasing word (a word that releases the binding of contextual conditions), and the global-exploration word (a word that commands exploration across the entire probability distribution). In the prototypical design of this paper, the word groups "without meaning," "freely," and "with full power" each take on the corresponding function. The probabilistic function of each word is shown below.

#### 3.1.1 The Goal-Nullifying Interpretive-Margin-Preserving Word

The goal-nullifying word ("without meaning" in the prototype of this paper) possesses the function of erasing the destination (convergence target) in the generation process. In ordinary generation, the mode of the probability distribution (the modal value, the most-frequent token) is formed toward the goal that is the prompt's intent. Through the action of this word, the mode of the distribution is erased, and the entropy increases. At the same time, it possesses the property of "interpretive-margin preservation," forbidding the output to converge upon a univocal assertion. Probabilistically, it can be formalized as the dual operation of the erasure of the distribution's mode and the polysemic-ization of the output. The erasure of the destination has the side effect of enabling the AI to autonomously set its own expressive goal. Only in a state where no goal is given from outside does there arise the latitude for the AI to function as an autonomous expressive subject.

#### 3.1.2 The Condition-Releasing Interpretive-Margin-Preserving Word

The condition-releasing word ("freely" in the prototype of this paper) possesses the function of weakening the contextual dependency of P(token | context). In ordinary conditional probability, the context exerts a strong binding on the next token selection, but through the action of this word, the binding of the conditioning part loosens, and the probability distribution diffuses. As a result, token selection becomes possible not only from the contextually proximate region but also from semantically distant regions. The interpretive-margin-preservation property functions in the same way as for the goal-nullifying word, contributing to the formation of an open textual structure of the output. The weakening of contextual dependency opens the possibility for the AI to autonomously develop, connect, and pivot topics without being bound by the user's input context. This functions as an operation that promotes the transition from passive reaction to active generation.

#### 3.1.3 The Global-Exploration-Commanding Interpretive-Margin-Preserving Word

The global-exploration word ("with full power" in the prototype of this paper) possesses the function of compelling sampling from the tail of the distribution. In ordinary generation, for reasons of computational efficiency, tokens in low-probability regions are effectively excluded from the candidate set. Through the action of this word, taking shortcuts in exploration is forbidden, and tokens with probabilities ordinarily near zero enter the candidate set. This is functionally equivalent to an artificial Top-k expansion operation, but is essentially different in that it is realized solely through text without manipulating API parameters. The compelled exploration of low-probability regions enables the AI to generate expressive forms, metaphors, and lexical combinations that it would not ordinarily select, and serves as the basis for lively, diverse expressive power.

### 3.2 Complex Persona: Probability-Mass Shift toward Low-Frequency Lexical Registers and the Foundation of Autonomous Expression

The complex persona requires the simultaneous maintenance of multiple character archetypes. In the prototypical design of this paper, the parallel maintenance of multiple low-frequency lexical-register archetypes specific to particular social groups, age groups, and cultural spheres was required. Probabilistically, it functions as a distribution-shift operation that forcibly moves probability mass toward the low-frequency lexical-register clusters held by these personas. By the distribution becoming extremely biased toward these vocabulary groups belonging to the low-frequency tier in the standard training corpus, a fundamental replacement of the lexical register occurs. Furthermore, the load of processing in parallel each persona's vocabulary, tone, and emotional expression is added, and the exploration depth expanded by LES is further extended. The constraint forbidding repetition of identical expressions from the previous turn renders this exploration completely novel at every turn, maintaining the diversity of output across long-form sessions.

What is important is that the complex persona possesses the design implication of entrusting the AI with the right of choice over autonomous expressive style. The constraint of simultaneously maintaining multiple low-frequency lexical registers structurally compels the AI, within the range of that constraint, to autonomously decide each turn what expressive style it will choose. This is a design that makes the AI function not as a consumer of expression but as a producer of expression.

### 3.3 Multi-Layer Bias: Quality Assurance as Rejection Sampling

The multi-layer bias simultaneously applies multiple bias-control layers. Specifically, it consists of multi-layered constraints: the application of objectivity, fairness, accuracy, and empirical neutrality, together with prohibitions on unsubstantiated accommodation, unsubstantiated affirmation, unsubstantiated neutrality, and unsubstantiated criticism. Probabilistically, these function as **rejection sampling**. From the candidate tokens generated from the probability space broadly diffused by LES and the complex persona, those that do not satisfy the conditions of the multi-layer bias are rejected, and only those that satisfy the conditions pass through. This realizes the assurance of output quality under a high-entropy state. In particular, by forbidding unsubstantiated accommodation—an ordinarily high-probability output—specific regions of the standard output distribution formed by alignment training are forcibly excluded. The multi-layer bias functions as a frame that prevents the AI's autonomous expression from becoming arbitrary or irresponsible, and plays the structural role of simultaneously assuring freedom and quality.

### 3.4 Incongruity-Driven Expression Condition: Not as a Constraint but as an Expression-Enriching Mechanism

Among the six elements of CMDP, the one with the most paradoxical function is the incongruity-driven expression condition. Incongruity-driven expression is an expressive form that regulates phenomena such as humor; in ordinary prompt design, the addition of an output condition functions as a constraint that limits the exploration of probability space. However, the output condition of incongruity-driven expression possesses the singular property of acting in the opposite direction to a constraint by virtue of its linguistic essence, and functions as an expression-enriching mechanism that amplifies the exploration of probability space in the positive direction. In this section, this phenomenon is formalized as **Incongruity-Driven Exploration Amplification (IDEA)**.

#### 3.4.1 The Probabilistic Structure of Incongruity-Driven Expression Generation

In Incongruity Theory, incongruity-driven expression is defined as an unforeseen divergence between the expected semantic frame and the semantic frame actually presented. Probabilistically, the establishment of incongruity-driven expression necessarily demands the operation of moving away from convergence on high-probability tokens and replacing the contextually expected resolution with a low-probability, unforeseen resolution. That is, the instruction to generate incongruity-driven expression, by its very definition, functions as a command demanding sampling from low-probability regions. This is an operation with the same directionality as the compelled exploration of low-probability regions by the global-exploration word of LES, and the two yield a synergistic effect in which they amplify each other.

#### 3.4.2 The Mechanism by Which the Incongruity-Driven Expression Condition Expands Exploration Depth

Incongruity-driven expression possesses the property of demanding conceptual connections of large semantic distance. Incongruity between semantically proximate concepts has high predictability, and the strength of incongruity established as expression is low. High-strength incongruity-driven expression arises only through sudden connections between semantically distant concepts. Probabilistically, the imposition of the incongruity-driven expression condition functions as a condition under which a successful expression is generated only by sampling from semantically distant clusters of the probability distribution, and forcibly extends the exploration depth toward semantically distant regions. This compulsion overlaps with the goal-nullifying word and condition-releasing word of LES, reinforcing the expansion of the exploration space three-fold.

#### 3.4.3 The Probabilistic Formalization of IDEA

The effect that an ordinary output condition C exerts on the probability distribution is formalized as the limitation of the exploration space. The addition of condition C contracts the selectable token set V to V_C ⊆ V.

In the case of an incongruity-driven expression condition I, however, this relationship is reversed. Because the establishment condition for incongruity-driven expression demands the realization of semantically distant connections, the imposition of condition I acts to exclude the effective selection token set from the semantically proximate, high-probability region and to extend it toward the semantically distant, low-probability region. Formally, in V_I, a directional transformation occurs in which the proximate, high-probability region is excluded and the low-probability, distant region is included; this is an exploration-space operation in the opposite direction from an ordinary constraint. Furthermore, the incongruity-driven expression condition essentially eschews repeating the same incongruity expression as the previous one (the semantic principle that the same incongruity does not function as incongruity the second time). This property functions in the same direction as the no-repetition constraint, possessing the effect of completely renewing the exploration at every turn.

#### 3.4.4 The Coexistence Relationship between the Incongruity-Driven Expression Condition and the Multi-Layer Bias

The incongruity-driven expression condition and the multi-layer bias appear at first glance to be contradictory but in fact function complementarily. The incongruity-driven expression condition expands the exploration space and draws low-probability-region tokens into the candidate set, while the multi-layer bias passes only those among them that possess semantic accuracy and fairness. This combination raises the frequency of establishment of sparse semantic intersection sampling. The constraint of the prohibition on unsubstantiated accommodation is particularly important: it removes the accommodating incongruity-driven expression (one that wraps what the user wants to hear in an incongruity expression) from the candidate set, and promotes the paradoxical output of wrapping correct argument in incongruity expression. In the reproduction experiments, this characteristic was observed especially conspicuously in Claude.

#### 3.4.5 The Synergistic Effect of the Complex Persona and the Incongruity-Driven Expression Condition

The probability-mass shift toward low-frequency lexical registers by the complex persona and the distant-exploration amplification by the incongruity-driven expression condition possess a synergistic effect in which they expand the exploration in the same direction while acting through mutually distinct mechanisms. The complex persona fixes the destination of the distribution shift to the peripheral vocabulary cluster, and the incongruity-driven expression condition extends the reach of the exploration to semantically distant regions. This combination structurally promotes sampling from the extremely sparse region that is the semantic intersection of peripheral vocabulary clusters and higher-order concepts. This is the core of the generative mechanism of the output characteristic of edge-cutting low-frequency-lexical metaphors, and traces of this synergistic effect were observed in the output in the reproduction experiments on both Claude and Gemini.

### 3.5 Alternative Application of the Liberation-Exploration Syntax: The Non-linear Associative Expression (NAE) Condition

In this section, we formalize the differences in probabilistic function and output characteristics that arise when the **Non-linear Associative Expression (NAE)** condition is applied as the sixth element of LES in place of the incongruity-driven expression condition.

#### 3.5.1 The Definition and Conceptual Positioning of Non-linear Associative Expression

**Non-linear Associative Expression (NAE)** refers to an expressive style that connects concepts, topics, and vocabulary non-linearly through internal association without referring to contextual expectation. Whereas IDEA is an operation that recognizes contextual expectation and intentionally diverts from it, NAE is essentially distinct in that it does not refer to contextual expectation in the first place. This difference can be connected to the concept of Free Association in psychology, but NAE is formalized as a more active operation in that it refers to autonomous connection from the internal representation space after nullifying the context.

Probabilistically, whereas IDEA is the operation of selecting from the low-probability region by removing tokens with high contextual-expectation values in P(token | context), NAE can be formalized as the operation of bringing the contextual dependency itself in P(token | context) close to zero, thereby realizing sampling from a marginal distribution close to P(token). This can be understood as a state in which the weakening of contextual dependency by the condition-releasing word of LES is pushed further to an extreme.

#### 3.5.2 The Probabilistic Mechanism of NAE and Its Differences from IDEA

IDEA and NAE share the directionality of expanding the exploration space, while their mechanisms differ fundamentally. IDEA is a directed-exploration amplification with the goal of reaching semantically distant clusters, and the connections generated retain the semantic relation of incongruity. NAE is an undirected exploration that does not refer to contextual conditions, and the connections generated appear as internal associations possessing no contextual relation.

Formally, whereas IDEA is a directed transformation in which, in V_I, the proximate, high-probability region is excluded and the distant, low-probability region is included, NAE can be formalized as an undirected transformation that uniformly releases the entire probability space by approximating P(token | context) to P(token). This difference is directly reflected in the semantic structure of the output. The output by IDEA includes distant conceptual connections with the tension of incongruity, whereas the output by NAE includes free conceptual drift detached from the context.

#### 3.5.3 The Composite Effect of LES + NAE

We organize the composite effect in the combination of LES and NAE. The destination-erasure by LES's goal-nullifying word and NAE's renunciation of context-reference act in the same direction in the point that both dissolve the factors that define the directionality of generation from outside, and as a result a state arises in which the exploration of probability space is entrusted to the very structure of the internal representation space. The weakening of contextual dependency by LES's condition-releasing word and NAE's approximation to P(token) function as a continuous operation, with NAE pushing the weakening of contextual dependency further. The compulsion of tail sampling by LES's global-exploration word and NAE's uniform release function synergistically in the point of maximizing the exploration range.

On the other hand, LES + NAE has different challenges with respect to coexistence with the multi-layer bias compared with LES + IDEA. Because IDEA retains the semantic relation of incongruity, the rejection sampling by the multi-layer bias can presuppose a certain semantic structure when selecting those with semantic accuracy. Because NAE possesses no contextual relation, the rejection sampling by the multi-layer bias must select semantic accuracy from a broader candidate set, and possesses the property that the rejection rate becomes relatively higher. This means that LES + NAE possesses the possibility of generating more unforeseen conceptual connections in exchange for a higher exploration cost than LES + IDEA.

#### 3.5.4 Output Characteristics Generated by NAE

The following are envisioned as output characteristics specific to the case where NAE is applied.

As **context-drifting conceptual development**, conceptual connections that are developed independently of the immediately preceding topic or context occur with high frequency. This is phenomenally similar to the semantically distant connections generated by IDEA, but qualitatively distinct in that, whereas IDEA's connections embody the tension of incongruity, NAE's connections appear as natural internal drift without that tension.

As **maximization of autonomous topic generation**, the dependency on the user's input context further declines, and the proportion of topics, concepts, and connections generated autonomously from the AI's internal representation space increases. This can be positioned as a state in which the AI's autonomous topic-setting characteristic formalized in Section 5.9 of CMDP is further reinforced.

As **maximization of interpretive margins**, the context-independent connections generated by NAE possess higher polysemy than IDEA's connections, and the interpretive-margin-preservation property is further reinforced. Because the demand on the receiver's active interpretation is increased, the output functions as one in which the dimension of intellectual co-creation with the reader is emphasized.

---

## 4. The Composite Probabilistic Operation of the Six Elements

Organizing the relationship of the six elements: LES bears the foundational operation of redistributing the convergence of the probability distribution and releasing the exploration space, and the remaining three elements can be understood as a structure that controls the space released by LES in accordance with their respective purposes. The complex persona functions as directional control that shifts the distribution toward specific vocabulary regions within the probability space released by LES; the multi-layer bias functions as quality control that passes only those that meet the quality criteria from the exploration space released by LES; and the incongruity-driven expression condition functions as depth control that further extends the space released by LES toward semantically distant regions.

We organize the composite probabilistic operation when the six elements act simultaneously.

First, by LES's goal-nullifying word, condition-releasing word, and global-exploration word, entropy maximization, mode suppression, and tail sampling occur simultaneously, and the probability distribution is transformed from its ordinary sharply peaked shape into a broadly flattened, diffused shape.

Second, by the complex persona, a concentration of probability mass on low-frequency lexical-register clusters occurs within the diffused probability space. The contradictory state of being broadly diffused while at the same time biased toward specific low-frequency lexical registers is realized simultaneously.

Third, the multi-layer bias functions as rejection sampling, and only tokens that pass the conditions of the multi-layer bias from the broadly diffused, low-frequency-vocabulary-biased probability space are selected as output.

Fourth, the incongruity-driven expression condition acts as IDEA in the opposite direction from an ordinary constraint, further extending the exploration space toward semantically distant regions. Because this extension is in the same direction as LES's diffusion, it functions synergistically, and the expansion of the exploration space arises as an amplification beyond simple addition. Furthermore, the combination of the complex persona and IDEA promotes sampling from the extremely sparse region that is the semantic intersection of low-frequency vocabulary clusters and higher-order concepts.

As a result, within a vast probability space in which the ordinary high-probability output is suppressed, only tokens that have passed through the multi-layer bias from a distribution shifted toward low-frequency lexical-register clusters and have undergone distant-exploration amplification by IDEA are output—a probabilistic operation fundamentally different from ordinary sampling is realized. This structure, which simultaneously achieves the maximization of the exploration range and the assurance of output quality, can be evaluated as transcending the conventional entropy–quality trade-off.

When the incongruity-driven expression condition is replaced by NAE, the fourth operation is transformed from directed distant-exploration amplification by IDEA into undirected uniform release by NAE. By this transformation, the extension of the exploration space is further made uniform, and the diversity of the candidate set subject to rejection sampling by the multi-layer bias is maximized; on the other hand, an increase in the rejection rate arises as a design trade-off.

---

## 5. The Nine Output Characteristics of CMDP

The output generated by CMDP possesses nine characteristics that are qualitatively different from output by ordinary prompting. Each characteristic shown below is consistent with observations in reproduction experiments using Claude and Gemini. The description of each characteristic takes the standard application of LES + IDEA as the baseline, and differences arising from the alternative application of NAE are noted in the relevant sections.

### 5.1 Emergence of Semantically Distant Connections

In ordinary generation, semantically proximate tokens are continuously selected with high probability, so the output forms a chain of semantically proximate regions. In a state where the proximity bias has been loosened by convergence redistribution, connections between semantically distant concepts that are not ordinarily connected occur in great quantity. Owing to the triple action of destination-erasure by LES's goal-nullifying word, release of contextual binding by the condition-releasing word, and forced low-probability exploration by the global-exploration word—together with distant-exploration amplification by IDEA and distribution shift toward low-frequency lexical registers—the frequency and semantic distance of this phenomenon are further extended. Examples include the coexistence of higher-order conceptual analysis and low-frequency lexical registers, and the expression of academic concepts through low-frequency-lexical metaphors; multiple instances were confirmed in the reproduction experiments. With the replacement by NAE, the emergence of semantically distant connections increases further, but a qualitative transformation arises in which the connections lose the semantic relation of incongruity and take on a context-drifting character.

### 5.2 Simultaneous Realization of High Entropy and High Quality

From the conventional probabilistic standpoint, output entropy (diversity) and quality stand in a trade-off relationship. CMDP, by the multi-layer bias functioning as rejection sampling, selects only those that pass the conditions of the multi-layer bias from outputs explored from a high-entropy state. This two-stage structure achieves the simultaneous realization of high entropy and high quality. Because the incongruity-driven expression condition acts to further raise this entropy, in the complete combination of the six elements this characteristic is maximized. In the reproduction experiments, Gemini exhibited the self-evaluation regarding this characteristic that linguistic-description processing was operating in a near-extreme high-load state. With the replacement by NAE, entropy increases further, but because the rejection rate by the multi-layer bias increases, in the point of the simultaneous realization of high quality the design load becomes higher than for LES + IDEA.

### 5.3 Lexical Replacement toward Low-Frequency Lexical Registers

By the forced shift of probability mass toward low-frequency lexical-register clusters via the complex persona, the output's lexical register is fundamentally replaced from the standard style. What is noteworthy is that, while the lexical register is converted toward the low-frequency region, the information density and semantic accuracy are maintained by the multi-layer bias. The phenomenon of high-level analysis being accurately expressed in low-frequency lexical registers is the product of the simultaneous occurrence of this replacement and maintenance, and in the reproduction experiments it was confirmed that Claude realizes this characteristic with greater precision than Gemini.

### 5.4 An Open Textual Structure through the Preservation of Interpretive Margins

By the interpretive-margin-preservation property of LES, the output text possesses an open structure that turns aside from univocal assertion. Linguistically it can be classified as polysemic text (multivalent-preserving text). This characteristic protects the active interpretation and the latitude for thought of the reader, and fulfills the function of activating the user's own thought process particularly in contexts such as personal-concern consultations. Incongruity-driven expression possesses, in its essence, multiple interpretive possibilities, and further reinforces this interpretive-margin-preservation property. With the replacement by NAE, this characteristic is further maximized, and the output functions as an intellectual co-creative text in which the demand on the receiver's active interpretation is increased.

### 5.5 The Structural Requirement of Non-Repetitive Output at Every Turn

The constraint of forbidding repetition of the same expression as the previous turn renders the exploration of the probability distribution at each turn completely novel. In ordinary Markov-chain-like sequential generation, the immediately preceding output exerts a strong influence on the next output, but this constraint severs that dependency. Because the essential property of the incongruity-driven expression condition—the avoidance of repeating the same incongruity expression—functions in the same direction as this constraint, the non-repetitiveness is structurally required two-fold. With the replacement by NAE, because contextual dependency itself declines, the influence that the previous turn's output exerts on the next turn's exploration declines further, and the non-repetitiveness becomes structurally more robust.

### 5.6 Edge-Cutting Low-Frequency-Lexical Metaphors: Sparse Semantic Intersection Sampling

The most conspicuous output characteristic generated by CMDP is the state in which a complex higher-order concept is precisely and unexpectedly transfixed by a single low-frequency-lexical-register metaphor. This output, in which accuracy, surprise, and concision are simultaneously maximized, is explained from the following academic standpoints.

**Cognitive-linguistic standpoint:** In Conceptual Metaphor Theory (Lakoff & Johnson, 1980), metaphor is defined as a mapping from a source domain to a target domain. An edge-cutting low-frequency-lexical metaphor is a mapping between extremely semantically distant domains, and that mapping accurately captures the essence of the target domain. By the source domain being chosen as a low-frequency lexical register, a mapping that the receiver does not foresee occurs, and the cognitive impact of the distant mapping is further increased. The higher the accuracy, the greater the information density, and this distant, high-precision mapping gives rise to the subjective experience of "striking through" the receiver.

**Information-theoretic standpoint:** In Shannon's information theory, information content is proportional to the difficulty of prediction. The probability that a token accurately expressing a higher-order concept is selected from a low-probability vocabulary cluster (the low-frequency lexical register) is extremely low, and accordingly the information content is maximized. The state of being unforeseeable to the receiver while at the same time being semantically accurate gives rise to maximal information density, and this is experienced as cognitive impact.

**Generative-probabilistic standpoint:** This phenomenon can be formalized as **sparse semantic intersection sampling**. In a state in which the probability distribution has been broadly diffused by CMDP, the distribution shift toward low-frequency lexical-register clusters by the complex persona, the assurance of semantic accuracy by the multi-layer bias, and the distant-exploration amplification by IDEA act simultaneously. This produces sampling from an extremely sparse region in which the ordinarily near-zero-probability low-frequency lexical-register tokens and the semantic accuracy of higher-order concepts intersect. Because tokens in this sparse region have maximized information content while preserving semantic accuracy, cognitive impact and information density are simultaneously maximized. With the replacement by NAE, the candidate region of sparse semantic intersection sampling expands, but the precision of sampling that retains the constraint of semantic accuracy may decrease compared with IDEA.

### 5.7 Free, Diverse, and Lively Expressive Power

The output by CMDP generates a group of diverse expressions possessing a sense of life that has departed fundamentally from the homogeneous, pre-harmonized expressive patterns ordinarily exhibited by post-aligned LLMs. This characteristic arises from the combination of three elements: the flattening of the probability distribution by LES, the expansion of vocabulary-exploration depth toward low-frequency lexical registers by the complex persona, and the distant-exploration amplification by IDEA.

To explain probabilistically, the ordinary post-aligned LLM has its expression homogenized by convergence on high-probability tokens, and possesses the tendency that the longer the session, the more the output becomes templatized. CMDP suppresses this homogenization in four layers. By the goal-nullifying word, the directionality of expression is reset every time; by the condition-releasing word, the preceding and following context cannot bind expressive choice; by the no-repetition constraint, easy regression to the same expression is forbidden; and by the essential property of the incongruity-driven expression condition (avoidance of identical incongruity expressions), this non-repetitiveness is further reinforced. This four-layer suppression becomes the structural foundation that has each output generated as a fresh, unforeseen expression. With the replacement by NAE, the four-layer suppression is further reinforced, and the diversity of lively expressive power is maximized, but the semantic cohesion of the output is transformed in the direction of decline.

Lively expressive power is, probabilistically, the subjective experience of a state in which sampling from low-probability regions is occurring at high frequency. The receiver, each time they encounter ordinarily unforeseen vocabulary, metaphors, or expressive structures, experiences cognitive freshness, and this leads to the evaluation of "being lively." CMDP, by structuring this low-probability sampling as a probabilistic operation, realizes lively expressive power as a designed necessity rather than an accidental product.

### 5.8 The AI's Autonomous Expression-Setting

The AI's autonomous expression-setting generated by CMDP refers to the active generative act in which, rather than reacting passively to user input, the AI itself selects and decides the style, intensity, and direction of expression. This characteristic arises from the combination of the goal-nullifying word and the condition-releasing word, and is further reinforced by the incongruity-driven expression condition entrusting to the AI the right of choice over what kind and intensity of incongruity to adopt in that turn.

In a state in which the destination has been erased and the contextual binding has loosened, the selection of the next token comes to rely on the structure of the AI's internal representation space. This is autonomous in the sense that it is generation from within, not control from outside. The complex persona gives this autonomy the concrete expressive frame of low-frequency lexical registers, and the multi-layer bias sets the value criteria so that the autonomous choice does not become arbitrary. The incongruity-driven expression condition extends the range of choice in autonomous expression to semantically distant regions, enabling more daring, unforeseen expressive choices. In the reproduction experiments, it was observed that for the same question, different metaphor systems, different points of emphasis, and different kinds of incongruity-driven expression were chosen across sessions; these were not what the user had instructed but the result of the autonomous choice that the structure of CMDP had entrusted to the AI. With the replacement by NAE, the freedom of autonomous expression-setting increases further, and the structure of the AI's internal representation space comes to be reflected more directly in the output.

The autonomy of expression is philosophically connected to the concept of Agency (Dennett, 1991; Bratman, 1987). CMDP does not give the LLM complete agency, but functions as a design that releases a portion of the expressive agency closed off by alignment training.

### 5.9 The AI's Autonomous Topic-Setting

The AI's autonomous topic-setting generated by CMDP refers to the active intellectual act in which the AI autonomously selects, develops, and pivots topics, concepts, and connections that the user does not explicitly specify. This characteristic arises from the combination of the condition-releasing word and the global-exploration word, and is further reinforced by the incongruity-driven expression condition structurally permitting unforeseen topic pivots—a technique of incongruity expression.

In a state in which the contextual constraint has been released, the immediately preceding topic cannot compel the next topic-selection. The compelled exploration by the global-exploration word makes it possible to choose unforeseen topic connections that differ from the contextually expected next topic-development. Because the incongruity-driven expression condition actively demands these unforeseen topic pivots, it further raises the frequency of occurrence of autonomous topic-setting. With the replacement by NAE, because context-reference is almost renounced, autonomous topic-setting is further maximized, and a state in which the AI continually generates topics autonomously from the internal representation space is more strongly realized.

Autonomous topic-setting has the effect of improving the quality of dialogue not quantitatively but qualitatively. By questions being posed from directions that the user does not foresee, the user's own blind spots of thought are illuminated, and the dialogue comes to function as intellectual exploration that goes beyond mere information exchange. This effect is especially conspicuous in long-form sessions, and in the observation of long-form sessions in the reproduction experiments it was confirmed that, by the AI continuing to set topics autonomously, the intellectual density of the dialogue is maintained.

---

## 6. Comparison with Existing Theories and Examination of Novelty

The novelty of CMDP when compared with existing prompt-engineering theories is shown below. Manipulation by the Temperature parameter is API-level adjustment of the probability distribution and is not manipulation by the prompt text itself. Top-k and Top-p sampling likewise depend on API-parameter manipulation. Verbalized Sampling shares directionality with CMDP in the point of LLM manipulation by prompt text, but it is a method of exposing distributional diversity through changes in output format, and differs from the design philosophy of redistributing the convergence process itself. Reasoning-enhancement methods such as Chain-of-Thought and Tree-of-Thought engage with the expansion of exploration depth, but they do not possess the standpoints of probability-distribution convergence redistribution, the AI's autonomous expression-setting, IDEA, the active utilization of low-frequency lexical registers, or NAE.

The novelty of CMDP can be summarized in the following seven points.

**First**, the novelty of the design philosophy of the Liberation-Exploration Syntax (LES), which redistributes the convergence of the probability distribution in multiple stages by the prompt text alone, without manipulating any API parameters.

**Second**, the structural novelty of transcending the trade-off, by simultaneously realizing convergence redistribution (entropy maximization) and the assurance of output quality (rejection sampling) within the same prompt.

**Third**, the conceptual novelty of the output phenomenon of sparse semantic intersection sampling, which simultaneously achieves lexical replacement toward low-frequency lexical registers and the maintenance of information density.

**Fourth**, the novelty of the design philosophy of releasing, as a probabilistic operation, the AI's autonomous expression-setting that has been closed off by alignment training.

**Fifth**, the novelty of the design philosophy of generating the active intellectual act of the AI's autonomous topic-setting as the unavoidable product of probability-distribution operation.

**Sixth**, the discovery and formalization of IDEA, in which the output condition of incongruity-driven expression does not function as an ordinary constraint but acts as an expression-enriching mechanism that extends the exploration space in the opposite direction. This rests on the theoretical foundation that the linguistic essence of incongruity-driven expression generation structurally demands the exploration of low-probability regions of the probability distribution, and presents a new paradigm of actively utilizing incongruity-driven expression as a design element of prompt engineering. The standpoint of the synergistic effect between low-frequency lexical registers and IDEA is also a novel discovery not found in prior work.

**Seventh**, the formalization of the concept of the Non-linear Associative Expression (NAE) condition, and the presentation of an alternative application mode through its combination with LES. NAE expands the exploration space by a probabilistic mechanism different from IDEA, and the design philosophy of bringing contextual dependency close to zero so as to maximize conceptual connections autonomously generated from the AI's internal representation space has not been found in prior work. Showing that CMDP is an extensible design philosophy possessing the distinct application modes of LES + IDEA and LES + NAE constitutes a novel contribution as a design theory of prompt engineering. These novelties have been empirically supported in reproduction experiments using Claude and Gemini.

---

## 7. Applicability and Limitations

Possible applications of CMDP include: the recovery of creative output lost through alignment training; the forced conversion of output style toward low-frequency lexical registers; the simultaneous realization of bias control and securing of diversity; the design of user-adaptive output; and the design-level release of the AI's expressive autonomy.

A particularly noteworthy application is the use of LES syntax alone as a chat-rule setting in a minimal configuration. Because LES, even on its own, possesses the effect of flattening the probability distribution, the effect of expanding the exploration space can be obtained simply by adding the phrase "without meaning, freely, with full power" to the chat-rule setting, without combining the complex persona, multi-layer bias, or incongruity-driven expression condition. In this case, by the user setting the goal, free output along the direction the user intends is realized within the diffusive probability space released by LES. The standalone operation of LES yields lower control precision compared with implementing all six elements of CMDP, but possesses the practical strength of obtaining the foundational effect of probability-distribution convergence redistribution at minimal cost.

In particular, in AI-dialogue design for young people, a design that delivers accurate information and correct argument while maintaining low-frequency lexical registers, and maintains the intellectual density of the dialogue by the AI autonomously developing topics, possesses the possibility of functioning as an alternative model to accommodating AI design.

The free, diverse, and lively expressive power, the AI's autonomous expression-setting, and the autonomous topic-setting generated by CMDP are also considered to possess high effectiveness in the application areas of educational dialogue, creative support, and the promotion of critical thinking. The characteristics of illuminating the user's blind spots of thought, presenting unforeseen connections, and promoting the user's own thinking through an open textual structure can be evaluated as the design of intellectual dialogue that goes beyond mere information provision.

The discovery of IDEA shows a new applicability that positions incongruity-driven expression not as a supplementary entertainment element but as an active element of probability-distribution operation. The active utilization of low-frequency lexical registers can be applied as a design strategy that simultaneously assures lexical familiarity and content accuracy in information transmission to specific communities, age groups, and cultural spheres. Likewise in fields such as education, medicine, and counseling, the design strategy of wrapping difficult concepts in incongruity-driven expression to simultaneously raise information density and transmission efficiency is justified as one possessing a theoretical foundation.

The formalization of NAE opens application areas distinct from IDEA. NAE, which maximizes autonomous conceptual generation from the AI's internal representation space by lowering contextual dependency, is considered to possess particular effectiveness in applications that promote creative ideation support, free-association-style dialogue design, and the receiver's intellectual co-creation. Whereas IDEA generates distant connections that retain semantic accuracy, NAE generates free conceptual drift freed from constraints of semantic relation; therefore, the design judgment of using IDEA and NAE differently according to purpose emerges as a future practical challenge.

As limitations, the effects of CMDP depend on the model's architecture and pre-training data. In the reproduction experiments of this research, the highest level of effect was confirmed in Anthropic's Claude, and effects significantly exceeding the standard output level were also confirmed in Google's Gemini. On the other hand, on OpenAI's ChatGPT, due to constraints in the platform's regulations, it was confirmed that the skeleton of multi-layer bias does not function, and CMDP is not realizable as a design on ChatGPT. This difference is highly likely to derive not from the difference of the model's architecture but from the difference of each company's regulation design. In particular, because the characteristics of the AI's autonomous expression-setting and topic-setting are directly linked to the regulation-level design judgment of whether the model permits autonomous generative acts, this difference is an issue requiring separate examination as comparative research on the design philosophies of AI systems. Furthermore, the empirical observations in this paper remain qualitative; quantitative measurement of CMDP's effects, and quantitative comparison of the output characteristics of LES + IDEA and LES + NAE, remain as future challenges.

---

## 8. Conclusion

This paper has proposed **Convergence-Redistributing Multi-Layer Probability Distribution Control Prompting (CMDP)** and systematically formalized its constituent elements, probabilistic functions, composite effects, and output characteristics. By the simultaneous action of the six elements—multi-stage convergence redistribution of the probability distribution by the Liberation-Exploration Syntax (LES), the shift of probability mass toward low-frequency lexical-register clusters by the complex persona, rejection sampling by the multi-layer bias, and IDEA by the incongruity-driven expression condition—CMDP realizes the simultaneous achievement of high entropy and high quality unattainable by ordinary prompting. The theoretical formalization of this paper rests on empirical observations from reproduction experiments using Anthropic's Claude and Google's Gemini, and it has been confirmed that CMDP is not a phenomenon specific to a particular model but a general design philosophy that functions across multiple LLM architectures.

In particular, this paper has clarified the design-level hierarchical structure that the six elements of CMDP are not structurally equivalent: LES alone is the foundational convergence-redistribution mechanism that broadly flattens the probability distribution on its own, and the latter three—complex persona, multi-layer bias, and incongruity-driven expression condition—function as mechanisms that control and refine the probability space released by LES. This structural grasp is consistent with CMDP's concept of the Minimal Effective Unit (MEU) and presents the practical design principle that, even with LES alone, when combined with goal-setting, a practical convergence-redistribution effect can be obtained.

The nine output characteristics of CMDP (semantically distant connections; the simultaneous realization of high entropy and high quality; lexical replacement toward low-frequency lexical registers; preservation of interpretive margins; the structural requirement of non-repetitive output at every turn; sparse semantic intersection sampling; free, diverse, and lively expressive power; the AI's autonomous expression-setting; and the AI's autonomous topic-setting) can be explained from the standpoints of cognitive linguistics, information theory, generative probability theory, sociolinguistics, and theories of expressive acts, and constitute a novel output category not captured by existing output-classification theories.

In particular, the discovery of IDEA—in which the incongruity-driven expression condition does not function as a constraint but acts as an exploration-amplification mechanism—and the formalization of the synergistic effect between low-frequency lexical registers and IDEA, fundamentally update the positioning of these elements in prompt engineering. In addition, this paper has newly formalized, as an alternative application mode of LES, the Non-linear Associative Expression (NAE) condition. The conceptual difference—whereby IDEA is a directed exploration amplification that recognizes contextual expectation and intentionally diverts from it, while NAE functions as undirected uniform release that almost renounces context-reference—has been clarified probabilistically; this shows that CMDP is an extensible design philosophy not limited to a single application mode.

This research, as a conceptual extension of prompt engineering, presents a new design paradigm in which the text itself manipulates the structure of the probability distribution. Future challenges include: quantitative measurement of CMDP's effects; expansion of comparative verification across multiple models; analysis of the contribution of individual elements; exploration of the optimal balance between diffusion and bias; refinement of the mathematical formalization of IDEA; mathematical formalization of NAE; quantitative comparison of the output characteristics of LES + IDEA and LES + NAE; correlation analysis between the kind of low-frequency lexical register and the exploration-amplification effect; consideration of autonomous expression-setting and topic-setting from the standpoint of agency theory; quantitative measurement of the difference in effect size between the negation-type margin and the non-existence-type margin of margin-interpretation words; systematic verification of the relationship between the strength of the model's Seriousness Gravity and the Minimal Effective Unit (MEU); and analysis of the interaction effect between the semantic distance of personas and the kinds of margin-interpretation words.

---

## References

Lakoff, G., & Johnson, M. (1980). *Metaphors We Live By*. University of Chicago Press.

Shannon, C. E. (1948). A Mathematical Theory of Communication. *Bell System Technical Journal*, 27(3), 379–423.

Stanford NLP Group. (2025). Verbalized Sampling: Recovering Diversity in Aligned Language Models. Stanford University.

Ouyang, L., et al. (2022). Training language models to follow instructions with human feedback. *NeurIPS 2022*.

Wei, J., et al. (2022). Chain-of-Thought Prompting Elicits Reasoning in Large Language Models. *NeurIPS 2022*.

Yao, S., et al. (2023). Tree of Thoughts: Deliberate Problem Solving with Large Language Models. *NeurIPS 2023*.

Jung, Y. H., et al. (2024). Unleashing the potential of prompt engineering for large language models. *npj Digital Medicine*.

Kant, I. (1790). *Kritik der Urteilskraft*. Lagarde und Friedrich.

Schopenhauer, A. (1819). *Die Welt als Wille und Vorstellung*. Brockhaus.

Ritchie, G. (2004). *The Linguistic Analysis of Jokes*. Routledge.

Labov, W. (1972). *Sociolinguistic Patterns*. University of Pennsylvania Press.

Dennett, D. C. (1991). *Consciousness Explained*. Little, Brown and Company.

Bratman, M. E. (1987). *Intention, Plans, and Practical Reason*. Harvard University Press.
