# System Design

## AdaptiveUI architecture

The paper organises AdaptiveUI into three main layers.

### 1. Browser environment

The browser-side layer observes the rendered page and injects changes. A content script uses DOM mutation monitoring to detect added or modified elements and retrieves computed styles for candidate text elements.

### 2. Machine-learning engine

For each relevant element, the system constructs features describing the visual and typographic context. The paper considers:

- foreground and background colour represented in a perceptually motivated space such as CIELAB
- luminance difference and approximate saturation
- font size, weight and style
- element type and interaction state
- contextual conditions such as text over images or gradients

The target is a continuous readability/legibility score. The paper proposes a lightweight ensemble regression approach, such as Random Forest or Gradient Boosting, to support low-latency inference and interpretable feature behaviour.

### 3. Optimisation module

If predicted readability is below the user's threshold, AdaptiveUI searches for an alternative foreground colour. The objective is to satisfy the readability requirement while minimising perceptual change from the original colour.

The paper describes a staged search beginning with lightness adjustment and relaxing chroma or hue when necessary. Candidate colours are evaluated using the learned readability predictor and perceptual distance.

## User profile

Personalisation is represented by a user profile containing a minimum readable contrast threshold and tolerances or constraints on hue, lightness and chroma changes. The paper also discusses the possibility of learning preferences from future behavioural feedback such as overrides.

## Runtime behaviour

The intended runtime sequence is:

```text
Rendered page
    ↓
DOM observation
    ↓
Style and context extraction
    ↓
Legibility prediction
    ↓
Below user threshold?
   /        \
 No          Yes
 |            ↓
Keep      Contrast search
              ↓
      Perceptual distance check
              ↓
       Style injection
```

This documentation describes the architecture presented in the paper. It is not a claim that the complete prototype source code is contained in this repository.
