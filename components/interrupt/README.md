# Interrupt Component

[![Badge](https://components.espressif.com/components/espp/interrupt/badge.svg)](https://components.espressif.com/components/espp/interrupt)

The `Interrupt` class provides APIs to register interrupt handlers for GPIO and
configure the interrupts. Interrupts can be configured to trigger on rising
edge, falling edge, high level, low level, or any change in the input signal. A
single interrupt object can manage multiple GPIO pins with separate callbacks
for each GPIO, or separte `Interrupt` objects can be created (though that uses
more memory and CPU as each `Interrupt` will has its own queue, ISR handler, and
task.

Finally, the `Interrupt` class is also designed to be subclassed if desired to
provide additional functionality, or it can of course be included as a member
within another class. The Button class provides a very simple implementation of
a subclass of `Interrupt`.

## Example

The [example](./example) shows how to use the `espp::Interrupt` class to configure
interrupts for one or more GPIO pins.

