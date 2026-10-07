For a function f:X→Y with domain X and codomain Y:

Injective (One-to-One / 단사):

Definition: Distinct domain elements map to distinct codomain elements.

$$\forall x_1, x_2 \in X, \quad x_1 \neq x_2 \implies f(x_1) \neq f(x_2)$$

Contrapositive: $f(x_1) = f(x_2) \implies x_1 = x_2$.

Example: $f(x) = 2x$ on $\mathbb{R}$ is injective, but $f(x) = x^2$ on $\mathbb{R}$ is not ($f(-1) = f(1)$).

Surjective (Onto / 전사):

Definition: Every element in the codomain is mapped to by at least one element in the domain. The range equals the codomain.

$$\forall y \in Y, \quad \exists x \in X \text{ such that } f(x) = y$$

Example: $f(x) = x^3$ on $\mathbb{R}$ is surjective, but $f(x) = x^2$ on $\mathbb{R} \to \mathbb{R}$ is not (negative reals are never hit).

Bijective (One-to-One Correspondence / 전단사):

Definition: A function that is both injective and surjective.

Significance: A function has a two-sided inverse f 
−1
 :Y→X if and only if it is bijective.
