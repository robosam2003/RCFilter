# Basic low pass RC filter implementation
This is a digital implementation of an analogue RC filter.

## Theory

<img src="https://github.com/robosam2003/RCFilter/blob/main/RCFilterDiagram">


We can infer that the differential equation for this system is:

$$
V_{in} = RC\frac{dV}{dt} + V_{out}
$$

Discretising using euler's method:

$$
\frac{dV_{out}}{dt} = \frac{V_{out}[n] - V_{out}[n-1]}{T}
$$

We obtain:

$$
V_{out} = V_{in}[n]\frac{T}{T+RC} + V_{out}[n-1]\frac{RC}{T+RC}
$$

This is calculated every time the `.update()` method is called, and is very computationally inexpensive.
w
## Operation

The RC filter is constructed with:
```cpp
RCFilter acc_x(8); // Cutoff frequency of 8Hz 
```

The filtered value is obtained by calling the `.update()` method:
```cpp
float out = acc_x.update(x);
```