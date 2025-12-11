
# Mini-project XAI -- RISE

## Authors
- BOUTRID Mourad
- KASSIMI Achraf
- Date: 11/12/2025

## Context & Motivation
RISE seeks to solve the "black box" problem of Convolutional Neural Networks (CNNs) by identifying exactly which parts of an image contribute most to a specific prediction. It generates an explanation for a single specific input instance rather than describing the general logic of the entire network, making it a local explanation method.

## RISE Intuition
- The "Swiss Cheese Experiment": Random masks are applied to an image to determine which parts are important for the model's prediction.
- Thousands of random masks are used, and the results are aggregated to create a saliency map.

## Mathematical Formulation
The saliency map \( S \) is computed as:

$$
S \approx \frac{1}{N\,p} \sum_{i=1}^{N} f(I \odot M_i)\, M_i
$$

Where:
- \( S \): Saliency map
- \( N \): Number of masks
- \( M_i \): Binary mask
- \( I \): Input image
- \( f()): Model output
- \( p \): Probability of pixel visibility

## Implementation Highlights
- **Setup and Model Training**: A simple CNN is trained on the MNIST dataset.
- **RISE Algorithm**: Generates random masks, applies them to the input, and aggregates results to compute the saliency map.
- **Visualization**: Heatmaps and overlays are used to interpret the model's predictions.

## Critical Analysis
### Strengths
- Model-agnostic and works with any classifier.
- Produces high-resolution and intuitive heatmaps.
- Robust to noise and adversarial perturbations.

### Limitations
- Computationally expensive due to the large number of forward passes required.
- Sensitive to hyperparameters like mask size and probability.
- May produce unrealistic masked images, leading to unpredictable model responses.

## Comparison with Other Methods
- **Advantages**: Higher spatial resolution and model-agnostic.
- **Disadvantages**: Slower and less theoretically grounded than methods like SHAP.

## Conclusion
RISE is a powerful tool for explaining black-box models but is computationally intensive. It is best suited for offline analysis and debugging rather than real-time applications.

## References

- Petsiuk et al., 2018. "RISE: Randomized Input Sampling for Explanation of Black-box Models."

