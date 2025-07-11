# MAX1704X I2C Battery Fuel Gauge Component

[![Badge](https://components.espressif.com/components/espp/max1704x/badge.svg)](https://components.espressif.com/components/espp/max1704x)

The MAX17048/MAX17049 ICs are tiny, micropower current fuel gauges for
lithium-ion (Li+) batteries in handheld and portable equipment. The MAX17048
operates with a single lithium cell and the MAX17049 with two lithium cells in
series.

The ICs use the sophisticated Li+ battery-modeling algorithm ModelGauge™ to
track the battery relative state-of-charge (SOC) continuously over widely varying
charge and discharge conditions. The ModelGauge algorithm eliminates
current-sense resistor and battery-learn cycles required in traditional fuel
gauges. Temperature compensation is implemented using the system
microcontroller.

The ICs automatically detect when the battery enters a low-current state and
enters low-power 3µA hibernate mode, while still providing accurate fuel
gauging. The ICs automatically exit hibernate mode when the system returns to
active state.

On battery insertion, the ICs debounce initial voltage measurements to improve
the initial SOC estimate, thus allowing them to be located on system side. SOC,
voltage, and rate information is accessed using the I2C interface. The ICs are
available in a tiny 0.9mm x 1.7mm, 8-bump wafer-level package (WLP), or a 2mm x
2mm, 8-pin TDFN package.

## Example

The [example](./example) shows how to use the MAX1704X driver to talk to the
MAX1704x and retrieve the current battery:
* Voltage
* Percentage
* Charge rate (%/hr)

