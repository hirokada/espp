# Thermistor Component

[![Badge](https://components.espressif.com/components/espp/thermistor/badge.svg)](https://components.espressif.com/components/espp/thermistor)

The Thermistor APIs provide a set of functions to read the temperature from a
thermistor. The thermistor stores the relevant information (from the datasheet)
such as the B value, the nominal resistance, circuit configuration (upper or
lower part of the voltage divider), the fixed resistor value, and the supply
voltage.

It uses these data to compute the measured resistance of the thermistor, from
which the temperature can then be calculated using the Steinhart-Hart equation.
See the [Wikipedia
article](https://en.wikipedia.org/wiki/Steinhart%E2%80%93Hart_equation) for more
information.

Using the Steinhart-Hart equation, the temperature can be calculated using the
following formula:

```math
    T = \frac{1}{\frac{1}{T_0} + \frac{1}{B} \\ln \frac{R}{R_0}}
```

where:

- $T$ is the temperature in Kelvin
- $T_0$ is the nominal temperature in Kelvin (e.g. 298.15 K, 25 °C)
- $B$ is the B ($\beta$, beta) value of the thermistor (e.g. 3950 K)
- $R$ is the resistance of the thermistor, measured in Ohm
- $R_0$ is the nominal resistance of the thermistor (e.g. 10000 Ohm at 25 °C)

Note: the `thermistor` component assumes that the thermistor is used within a
voltage divider circuit, with a fixed resistor. The component can be configured
so that either the thermistor or the fixed resistor is the upper part of the
voltage divider.

## Example

The [example](./example) shows how to use the `thermistor` component to compute
the temperature from a temperature sensitive resistor (thermistor) -
specifically negative temperature coefficient (NTC) thermistors.
