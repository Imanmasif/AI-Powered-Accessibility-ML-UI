# AI-Powered Accessibility: Evaluating the Role of Machine Learning in Inclusive User Interface Design

**Springer AI-HCI 2026 | Research paper companion repository**

[![DOI](https://img.shields.io/badge/DOI-10.1007%2F978--3--032--31048--4__6-blue)](https://doi.org/10.1007/978-3-032-31048-4_6)

## Overview

This repository accompanies the paper **AI-Powered Accessibility: Evaluating the Role of Machine Learning in Inclusive User Interface Design**, published in *Artificial Intelligence in HCI*, Lecture Notes in Computer Science, volume 16746, Springer, 2026.

The work introduces **AdaptiveUI**, a browser-based accessibility approach that uses supervised machine learning to estimate text legibility and then performs real-time colour-contrast adjustments within active web interfaces.

The central idea is to move beyond accessibility tools that only identify problems. AdaptiveUI is designed to detect low-legibility elements during interaction, find a minimally disruptive colour adjustment, and apply the change directly to the rendered interface while considering user-specific accessibility thresholds.

This repository is maintained as a research companion to the publication. It documents the research concept, system design, modelling approach, and evaluation framework. It should not be interpreted as a claim that a production-ready accessibility extension is maintained here.

## Research problem

Many accessibility tools operate as static checkers or developer-facing diagnostics. The paper addresses a different problem: how machine learning can support **real-time, user-oriented remediation** while a person is actually interacting with a web page.

The proposed approach focuses specifically on colour contrast and readability. It does not attempt to solve every dimension of digital accessibility.

## AdaptiveUI at a glance

The proposed system has three main layers:

1. **Observation layer** — monitors the rendered page and identifies relevant interface elements and style changes through the browser DOM.
2. **Prediction layer** — uses a supervised ML model to estimate a continuous legibility score from colour, typography, and contextual features.
3. **Optimisation layer** — searches for a new foreground colour that meets the user's readability threshold while keeping perceptual change as small as possible.

The approach is designed to operate client-side, allowing it to work with dynamically rendered pages without requiring changes to the website's server-side code.

## Machine learning approach

The paper describes a lightweight supervised regression approach rather than a large deep-learning model. The feature design considers:

- foreground and background colour information in a perceptually motivated colour space
- luminance difference and saturation
- font size, weight, and style
- element type and interaction state
- contextual conditions such as text over images or gradients

An ensemble model such as **Random Forest or Gradient Boosting** is considered because the system requires low-latency inference and interpretable feature behaviour.

## Contrast optimisation

When predicted readability falls below a user-specific threshold, AdaptiveUI performs a constrained search for an alternative colour. The search prioritises minimal perceptual change while attempting to satisfy the required readability level.

The paper combines:

- supervised readability prediction
- perceptually guided colour adjustment
- user-specific thresholds
- runtime DOM/style updates
- accessibility-oriented constraints

This makes the work different from a conventional static contrast checker or an offline colour recommendation tool.

## Personalisation

A key part of the proposed design is that accessibility needs are not assumed to be identical for every user. The paper describes a user profile that can represent a minimum readable contrast threshold together with preferences or constraints on colour changes.

Future versions could learn or refine these preferences from user behaviour, such as overrides or disabled adjustments, while preserving user control.

## Evaluation

The paper describes an evaluation using a within-subject comparison between:

- **Baseline:** the original interface without adaptive contrast correction
- **Adaptive:** the interface with AdaptiveUI's real-time contrast adjustments

The evaluation focuses on visually impaired users, with a smaller sighted control group considered for detecting unintended usability effects.

The primary measures are:

- task completion time
- task success
- perceived readability

Secondary measures include error rates, the amount of interface modification, perceptual colour distance, trust, and acceptability.

The paper reports improvement in task performance, error rates, and perceived readability under the adaptive condition. The work also discusses limitations and the need for broader evaluation beyond colour contrast.

## Standards and accessibility scope

The research is aligned with the broader WCAG accessibility context and focuses on colour contrast and readability during interaction. It is intentionally narrower than a complete accessibility framework.

Future work identified in the paper includes extending the approach toward:

- typography and text scaling
- spacing and layout adaptation
- semantic hierarchy
- motion reduction
- alternative text and other accessibility dimensions
- richer user-specific calibration
- semantic-aware optimisation using design-system or ARIA information

## Repository scope

The public repository currently serves as a **research documentation companion** to the published work. It does not contain a full production browser-extension codebase, participant-level data, or private research material.

For the complete technical formulation, implementation details, evaluation design, limitations, and references, please refer to the published chapter.

## Publication

**AI-Powered Accessibility: Evaluating the Role of Machine Learning in Inclusive User Interface Design**  
Danish Khan, Irfan Ahmed, Iman Muhammad Asif  
In *Artificial Intelligence in HCI*, Lecture Notes in Computer Science, vol. 16746, Springer, 2026, pp. 71–90.  
DOI: https://doi.org/10.1007/978-3-032-31048-4_6

## Citation

```bibtex
@inproceedings{khan2026accessibility,
  title={AI-Powered Accessibility: Evaluating the Role of Machine Learning in Inclusive User Interface Design},
  author={Khan, Danish and Ahmed, Irfan and Asif, Iman Muhammad},
  booktitle={Artificial Intelligence in HCI},
  series={Lecture Notes in Computer Science},
  volume={16746},
  pages={71--90},
  publisher={Springer, Cham},
  year={2026},
  doi={10.1007/978-3-032-31048-4_6}
}
```

## Repository note

This repository is maintained as a concise research companion to the publication. The published chapter remains the primary source for the complete research methodology, system formulation, evaluation plan, results, limitations, and references.