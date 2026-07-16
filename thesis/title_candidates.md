# Thesis Title Candidates

Current title (`main.tex:23`): **"Reinforcement Learning with NEAT in Multitask Environments"**

Problem: it frames RL as the topic, when the Brax locomotion tasks are just the test bed.
The actual contribution is one evolved network solving two tasks simultaneously, and whether
heterogeneous per-neuron activations (HA-NEAT) help compared to standard NEAT.

Note: results are a null finding — prefer neutral verbs ("comparing", "evaluating") over
anything implying HA-NEAT wins.

## A. The comparison as the headline (most honest to what was done)

1. *Homogeneous versus Heterogeneous Activation Functions in Neuroevolution: Comparing NEAT and HA-NEAT on Multi-Task Control*
2. *NEAT versus HA-NEAT: Evolving Multi-Task Controllers with Homogeneous and Heterogeneous Activation Functions*
3. *Does Activation Diversity Help? An Empirical Comparison of NEAT and HA-NEAT in Multi-Task Environments*
   - Question titles are bold but fit a null result well — the answer is "not significantly".

## B. Multi-task as the headline

4. *Evolving a Single Network for Multiple Tasks: NEAT and HA-NEAT on Simultaneous Locomotion Control*
5. *Multi-Task Neuroevolution: Evaluating Heterogeneous Activation Functions in NEAT for Joint Control of Hopper and Walker2D*
6. *One Genome, Two Tasks: Multi-Task Neuroevolution with NEAT and Heterogeneous Activations*
   - Catchy colon-free first clause; some committees find it too informal.

## C. Activation heterogeneity as the headline (frames it as the research question)

7. *Heterogeneous Activation Functions in Multi-Task Neuroevolution: A Comparison of NEAT and HA-NEAT* ⭐ **recommended**
8. *The Role of Activation Function Diversity in Multi-Task Neuroevolution*
9. *Evolving Activation Functions for Multi-Task Control: An Evaluation of HA-NEAT against NEAT*

## D. Control setting visible, without leading with "Reinforcement Learning"

10. *Multi-Task Continuous Control with Neuroevolution: Comparing NEAT and HA-NEAT*
    - Strongest alternative if the control domain should be visible.
11. *Neuroevolution for Simultaneous Locomotion Tasks: Homogeneous versus Heterogeneous Activations*

## Recommendation

**#7** — names the independent variable (activation heterogeneity), the setting
(multi-task neuroevolution), and the method comparison, without promising a positive
result and without the RL framing.

## Knobs to turn on any candidate

- "Multi-Task" vs "Multitask" — pick one and use it consistently (the thesis text currently uses both).
- Whether to name the environments (Hopper/Walker2D): concrete but dates the title.
- Whether "neuroevolution" or "NEAT" carries the main clause.
