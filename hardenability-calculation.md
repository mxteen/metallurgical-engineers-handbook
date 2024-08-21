# Hardenability calculation

Hardenability refers to the ability of steel to harden to a certain depth when
quenched from its austenitizing temperature. It is typically measured by
assessing the extent or depth of hardness in a standardized test specimen of
fixed size and shape after a controlled quenching process. In the end-quench
test, hardenability is determined by the distance from the quenched end of the
specimen that corresponds to a specified hardness level.

The test involves quenching one end of a cylindrical specimen, 1.0 inch in
diameter, in water and then measuring the hardness response as it varies with
distance from the quenched end.

## Grossman method described in ASTM A255

### Overview

This method of Jominy Hardenability calculation from the chemical ideal
diameter (DI) on a steel is based on the original work of M. A. Grossman [1]
and described in ASTM A 255 standard [2].
The calculation method described here is applicable to the following range
of chemical compositions:

| Element | Range, %  |
|---------|-----------|
| C       | 0.10–0.70 |
| Si      | 0.15–0.60 |
| Mn      | 0.50–1.65 |
| Cr      | ≤ 1.35    |
| Ni      | ≤ 1.50    |
| Cu      | ≤ 0.35    |
| Mo      | ≤ 0.55    |
| V       | ≤ 0.20    |

> However, to facilitate melting process control for higher alloy steels,
> Hardenability Multiplying Factors have been included for calculating the DI
> within the following chemical composition ranges:
> <cite>ASTM A 255</cite>

| Element | Range, %  |
|---------|-----------|
| C       | 0.01–0.90 |
| Si      | 0.01–2.00 |
| Mn      | 0.01–1.95 |
| Cr      | 0.01-2.50 |
| Ni      | 0.01-3.50 |
| Cu      | 0.01-0.55 |
| Mo      | 0.01-0.55 |
| V       | 0.01-0.20 |
| Zr      | 0.01-0.25 |

The procedure of hardennability curve calculation is the following.
1. First the ideal critical diameter should be calculated. To do this we need
to
    - Calculate the multiplying factor for each element.
    - Multply all the factors obtained above to obtain DI value in inches.
    - Convert the DI result to milimiters.

2. Then we need to calculate the hardness at the quenched end of the specimen.
3. Then using DI value to calculate a set of denominators for each distance
from the quenched end `(1.5, 3, 5, 7, 9, 11, 13, 15, 20, 25, 30, 40, 45, 50 mm)`.


### 1. DI Calculation for Non-Boron Steels
    TODO: describe the method applicable to boron steels

This calculation uses a set of hardenability factors for each alloying element
in the composition, which are multiplied together to determine the DI value in
inches ($DI_{in}$).
Only multiplying factors for DI in inch-pound units are provided for simplicity.
The effects of phosphorus and sulfur are not considered, as they tend to offset
each other. An austenitic grain size of No. 7 is assumed, as most steels with
controlled hardenability are produced using fine-grain practices. Experience
shows that a high percentage of heats conform to this grain size.

1. **Carbon Factor**:

```math
mf_C = \left\{
    \begin{array}{ll}
        0.54 \times C, & \text{if } 0.01 \leq C \leq 0.39 \\
        0.171 + 0.001 \times C + 0.265 \times C^2, & \text{if } 0.39 < C \leq 0.55 \\
        0.115 + 0.268 \times C - 0.038 \times C^2, & \text{if } 0.55 < C \leq 0.65 \\
        0.143 + 0.2 \times C, & \text{if } 0.65 < C \leq 0.75 \\
        0.062 + 0.409 \times C - 0.135 \times C^2, & \text{if } 0.75 < C \leq 0.90 \\
    \end{array}
\right.
```

2. **Silicon Factor**:
```math
mf_{Si} = 0.7 \times Si + 1
```

3. **Manganese Factor**:
```math
mf_{Mn} = \left\{
    \begin{array}{ll}
        3.3333 \times Mn + 1, & \text{if } Mn \leq 1.2 \\
        5.1 \times Mn - 1.12, & \text{if } Mn > 1.2 \leq 1.95 \\
    \end{array}
\right.
```

4. **Chromium Factor**:

```math
mf_{Cr} = 2.16 \times Cr + 1

```

5. **Nickel Factor**:
```math
mf_{Ni} = \left\{
    \begin{array}{ll}
        0.363 \times Ni + 1, & \text{if } 0 \leq Ni \leq 1.5 \\
        0.3211 + 1.4501 \times Ni - 0.6119 \times Ni^2 + 0.1253 \times Ni^3, &
        \text{if } Ni > 1.5 \leq 3.5 \\
    \end{array}
\right.

```

6. **Copper Factor**:
```math
mf_{Cu} = 0.365 \times Cu + 1

```

7. **Molybdenum Factor**:
```math
mf_{Mo} = 3 \times Mo + 1

```

8. **Vanadium Factor**:
```math
mf_{V} = 1.73 \times V + 1

```

9. **Zirconium Factor**:
```math
mf_{Zr} = 2.5 \times Zr + 1

```

An example of a $DI_{in}$ calculation for an SAE 4118 modified steel is
provided below. The chemical composition of the steel along with the
corresponding multiplying factors for each element are listed in the table.

Chemical Composition and Multiplying Factors

| **Element**    | **% Composition** | **Multiplying Factor** |
|----------------|-------------------|------------------------|
| Carbon (C)     | 0.22              | 0.119                  |
| Manganese (Mn) | 0.80              | 3.667                  |
| Silicon (Si)   | 0.18              | 1.126                  |
| Nickel (Ni)    | 0.10              | 1.036                  |
| Chromium (Cr)  | 0.43              | 1.929                  |
| Molybdenum (Mo)| 0.25              | 1.75                   |
| Copper (Cu)    | 0.10              | 1.04                   |
| Vanadium (V)   | 0.05              | 1.09                   |


To calculate the $DI_{in}$ value, the multiplying factors for each alloying
element are multiplied together:

```math
DI_{in} = 0.119 \times 3.667 \times 1.126 \times 1.036 \times 1.929 \times 1.75
\times 1.04 \times 1.09 = 1.95 \, \text{in.}
```
Converting inches to millimeteres.
```math
DI = DI_{in} \times 25.4
```

### 2. Initial hardness calculation
The initial hardness is determined solely by the carbon content and is
independent of hardenability. This value represents the martensite hardness.

```math
HRC_M = 33.087 + 50.723 \times C + 33.662 \times C^2 - 2.7048 \times
C^3 - 107.02 \times C^4 + 43.523 \times C^5
```

### 3. Hardenability Curve Calculation

The hardness at other positions along the end-quench specimen is found by
dividing the initial hardness by the appropriate factor. The formulas for these
factors are provided below.

To calculate the hardness at a specific distance from the quenched end use the
following formula:

```math
HRC_d = \frac{HRC_M}{df}
```

Here:
- $HRC_M$ is the initial hardness, which is a function of carbon content.
- $df_k$ is the denominator for the distance $k$ millimeters from the quenched
end and is computed using the polynomial coefficients:

```math
df_k = \sum_{i=0}^{5} \text{coeff}_i \times DI^i
```

```math
   df_3 = 0.170547 + 0.173925 \times DI - 0.0109281 \times DI^2
   + 3.13863 \times 10^{-4} \times DI^3 - 4.32086 \times 10^{-6} \times DI^4
   + 2.31674 \times 10^{-8} \times DI^5
```
```math
   df_5 = 3.03987 - 0.0855161 \times DI + 0.00138048 \times DI^2
   - 9.98717 \times 10^{-6} \times DI^3 + 2.64963 \times 10^{-8} \times DI^4
   + 5.46044 \times 10^{-12} \times DI^5
```
```math
   df_7 = 4.32366 - 0.134451 \times DI + 0.00228151 \times DI^2
   - 1.96250 \times 10^{-5} \times DI^3 + 8.35338 \times 10^{-8} \times DI^4
   - 1.38456 \times 10^{-10} \times DI^5
```
```math
   df_9 = 4.46324 - 0.0992003 \times DI + 0.00119387 \times DI^2
   - 7.40686 \times 10^{-6} \times DI^3 + 2.26087 \times 10^{-8} \times DI^4
   - 2.46815 \times 10^{-11} \times DI^5
```
```math
   df_{11} = 4.40915 - 0.0792024 \times DI + 6.74319 \times 10^{-4} \times DI^2
   - 1.97223 \times 10^{-6} \times DI^3 - 3.21758 \times 10^{-9} \times DI^4
   + 2.08025 \times 10^{-11} \times DI^5
```
```math
   df_{13} = 4.60261 - 0.0820023 \times DI + 7.18416 \times 10^{-4} \times DI^2
   - 2.52800 \times 10^{-6} \times DI^3 + 2.30089 \times 10^{-10} \times DI^4
   + 1.25368 \times 10^{-11} \times DI^5
```
```math
   df_{15} = 5.01595 - 0.0957696 \times DI + 9.56240 \times 10^{-4} \times DI^2
   - 4.62213 \times 10^{-6} \times DI^3 + 8.92787 \times 10^{-9} \times DI^4
   - 8.74859 \times 10^{-13} \times DI^5
```
```math
   df_{20} = 5.51133 - 0.104310 \times DI + 1.15299 \times 10^{-3} \times DI^2
   - 7.51801 \times 10^{-6} \times DI^3 + 2.75126 \times 10^{-8} \times DI^4
   - 4.3110 \times 10^{-11} \times DI^5
```
```math
   df_{25} = 6.15369 - 0.127486 \times DI + 1.57885 \times 10^{-3} \times DI^2
   - 1.12233 \times 10^{-5} \times DI^3 + 4.21359 \times 10^{-8} \times DI^4
   - 6.42460 \times 10^{-11} \times DI^5
```
```math
    df_{30} = 7.16001 - 0.171328 \times DI + 2.42820 \times 10^{-3} \times DI^2
    - 1.91259 \times 10^{-5} \times DI^3 + 7.67320 \times 10^{-8} \times DI^4
    - 1.21571 \times 10^{-10} \times DI^5
```
```math
    df_{35} = 8.46964 - 0.229424 \times DI + 3.54915 \times 10^{-3} \times DI^2
    - 2.97166 \times 10^{-5} \times DI^3 + 1.24831 \times 10^{-7} \times DI^4
    - 2.0543 \times 10^{-10} \times DI^5
```
```math
    df_{40} = 9.13657 - 0.252296 \times DI + 3.94419 \times 10^{-3} \times DI^2
    - 3.33383 \times 10^{-5} \times DI^3 + 1.41462 \times 10^{-7} \times DI^4
    - 2.35541 \times 10^{-10} \times DI^5
```
```math
    df_{45} = 8.84696 - 0.223317 \times DI + 3.25787 \times 10^{-3} \times DI^2
    - 2.62930 \times 10^{-5} \times DI^3 + 1.08190 \times 10^{-7} \times DI^4
    - 1.76244 \times 10^{-10} \times DI^5
```
```math
    df_{50} = 8.10202 - 0.171039 \times DI + 2.12643 \times 10^{-3} \times DI^2
    - 1.52754 \times 10^{-5} \times DI^3 + 5.78179 \times 10^{-8} \times DI^4
    - 8.79890 \times 10^{-11} \times DI^5
```

## Method described in SEP 1664
    TODO: describe SEP 1664 [3]

## References
1. Grossman, M. A., Hardenability Calculated from Chemical Composition, .AIME Transactions, Vol 150, 1942, pp. 227–259 (2) Banerji, S. K., and Morral, J. E., Boron in Steel , AIME, Warrentown, Pa, 1980, pp. 106–126
2. ASTM A255 − 10 (2014) Standard Test Methods for Determining Hardenability
of Steel
3. SEP 1664 Ermittlung von Formeln durch multiple Regression zur Berechnung der Härtbarkeit im Stirnabschreckversuch aus der chemischen Zusammensetzung von Stählen