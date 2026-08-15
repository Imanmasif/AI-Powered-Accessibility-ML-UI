# Research Summary

## Paper

**AI-Powered Accessibility: Evaluating the Role of Machine Learning in Inclusive User Interface Design**

Danish Khan, Irfan Ahmed, Iman Muhammad Asif. Published in *Artificial Intelligence in HCI*, Lecture Notes in Computer Science, volume 16746, Springer, 2026, pp. 71–90.

DOI: https://doi.org/10.1007/978-3-032-31048-4_6

## Research problem

The paper addresses a gap between static accessibility checking and accessibility support that can respond during real user interaction. Existing contrast checkers can identify problems, but they generally do not provide personalised, real-time correction of rendered interfaces.

## Proposed contribution

The paper introduces **AdaptiveUI**, a browser-based accessibility approach that combines supervised machine learning for legibility prediction with constrained colour-contrast optimisation. The system is designed to detect low-legibility text, search for a minimally changed foreground colour that satisfies a user-specific readability threshold, and inject the resulting style into the active page.

## Core workflow

1. Observe rendered interface elements through the browser DOM.
2. Extract colour, typography and contextual features.
3. Predict a continuous legibility score.
4. Compare the prediction with a user-specific threshold.
5. Search for a suitable alternative colour in a perceptually meaningful space.
6. Apply the selected adjustment to the rendered interface.

## Scope

The work focuses on colour contrast and readability. It does not claim to solve all web-accessibility problems. Typography scaling, spacing, semantic hierarchy, motion reduction, alternative text and broader accessibility dimensions are identified as future extensions.

## Evaluation design

The paper describes a within-subject comparison between an unmodified baseline interface and an AdaptiveUI condition. The evaluation is designed around visually impaired participants, with a smaller sighted control group to identify unintended usability effects. Measures include task completion time, task success, error rates, perceived readability, effort, satisfaction, trust and acceptability.

The paper reports improvement in task performance, error rates and perceived readability under the adaptive condition. It does not provide a numerical result table in the repository, so no numerical participant-level results are reproduced here.

## Important repository note

This document is a faithful research summary of the published paper. It does not claim that the public GitHub repository contains the full browser extension, participant-level data or private study materials. The publication remains the authoritative source for the complete technical and experimental description.
