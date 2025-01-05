# RoPE: ENHANCED TRANSFORMER WITH ROTARYPOSITION EMBEDDING

## Overview

Rotary Position Embedding (RoPE) is a novel method for encoding relative positional information into transformer-based models. Unlike traditional position encoding methods that add positional information to embeddings, RoPE encodes relative positions by rotating word embeddings in a multi-dimensional space using a rotation matrix. This rotation is based on the token's position and a predefined angle, allowing the model to inherently capture relative

## **The Math**

_Rotary encoding transforms pairs of features by rotating in the 2D plane. That is, it organizes the d features as d/2
pairs. Each pair can be considered a coordinate in a 2D plane, and the encoding will rotate it by an angle depending on the position of the token._

$$
\text{Let } x_m^{(1)} \text{ and } x_m^{(2)} \text {be two features of the key or}\\
 \text{query of any head at position m.}\\
 \text{For simplicity assume x has only two features. Then the transformation is:}
$$

$$
\text{RoPE}(x_m^{(1)}, x_m^{(2)}, m) =
\begin{bmatrix}
\cos(m\theta) & -\sin(m\theta) \\
\sin(m\theta) & \cos(m\theta)
\end{bmatrix}
\begin{bmatrix}
x_m^{(1)} \\
x_m^{(2)}
\end{bmatrix}
= \begin{bmatrix}
x_m^{(1)}\cos(m\theta) - x_m^{(2)}\sin(m\theta) \\
x_m^{(2)}\cos(m\theta) + x_m^{(1)}\sin(m\theta)
\end{bmatrix}
$$

$$ \Theta = \theta_i = 10,000^{-\frac{2(i-1)}{d}} , where ( i \in [1, 2, ..., 2d] ) \text{ for the ( 2d ) pairs of features.}$$
