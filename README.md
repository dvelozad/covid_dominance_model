# COVID Variant Dominance Model Explanation

This document provides a detailed explanation of the mathematical model used for fitting the dominance data of each COVID variant. The core of this model is encapsulated in the `ModelFunc` class, which utilizes a specific function inspired by the derivative of the sigmoid function.

## Mathematical Model

The function used to model the dominance of COVID variants over time is defined as:

$$ D_i(x) = \frac{q_i(x)}{\sum_i{q_i(x)}}$$

with $q_i(x)$ defined as:
$$q_i(x) =  \times \left( \frac{1}{1 + e^{-(a_i x + b_i)}} \right) \times \left( 1 - \frac{1}{1 + e^{-(c_i x + d_i)}} \right)$$


Where:
- $x$ represents the days since the start date.
- $a_i, b_i, c_i, d_i$ are parameters of the variant $i$ to be estimated through the fitting process and modulate the shape of the curve, influencing its growth rate, inflection points, and saturation levels.

## Inspiration from the Sigmoid Function

The model is inspired by the derivative of the sigmoid function, which is known for its S-shaped curve. The sigmoid function, denoted as $\sigma(x)$, is commonly used in logistic regression and neural networks to model probabilities and binary outcomes. Its derivative represents the rate of change of the curve, which is useful for modeling growth processes that undergo acceleration and deceleration phases.

The use of two sigmoid components in the function allows for modeling the dynamics of COVID variant dominance with flexibility. The first component, $\frac{1}{1 + e^{-(a x + b)}}$, models the initial growth phase of the variant, while the second component, $1 - \frac{1}{1 + e^{-(c x + d)}}$, accounts for the eventual decline or saturation in dominance as other factors or variants come into play.

## Objective

The primary objective of this mathematical model is to fit the dominance data of each COVID variant accurately. By adjusting the parameters $a, b, c, d$, the model can be tailored to reflect the unique growth and decline patterns of different variants over time. The fitting process involves minimizing the mean squared error between the model's predictions and the actual data, ensuring an optimal representation of the dominance trends.