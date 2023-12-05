# MAX17048 Zephyr driver
*The MAX17048 is a tiny, micropower current fuel gauge for lithium-ion (Li+) batteries in handheld and portable equipment.*

Based on an awesome work of David Schiller.
There is also an official [MAX17048 driver using Fuel Gauge API](https://docs.zephyrproject.org/latest/samples/fuel_gauge/max17048/README.html), but it lacks some important features and the API itself is still considered experimental and is not stable.

## Supported Zephyr versions
* 3.3.0 (February 2023)
## Usage
### Module installation
Add this project to your `west.yml` manifest:
```yaml
- name: MAX17048
  path: modules/MAX17048
  revision: refs/tags/zephyr-v3.3.0
  url: https://github.com/nobodyguy/MAX17048_zephyr_driver
```

So your projects should look something like this:
```yaml
manifest:
  projects:
    - name: zephyr
      url: https://github.com/zephyrproject-rtos/zephyr
      revision: refs/tags/zephyr-v3.3.0
      import: true
    - name: MAX17048
      path: modules/MAX17048
      revision: refs/tags/zephyr-v3.3.0
      url: https://github.com/nobodyguy/MAX17048_zephyr_driver
```

This will import the driver and allow you to use it in your code.

Additionally make sure that you run `west update` when you've added this entry to your `west.yml`.

### Driver configuration
Enable sensor driver subsystem and MAX17048 driver by adding these entries to your `prj.conf`:
```ini
CONFIG_SENSOR=y
CONFIG_I2C=y
CONFIG_MAX17048=y
```

Define MAX17048 in your board `.overlay` like this example:
```dts
/{
	fuel_gauge: max17048@36 {
        status = "okay";
        compatible = "maxim,max17048";
        enable-sleep;
        reg = <0x36>;
};
};
```

### Driver usage
```c
// TODO
```
Relevant `prj.conf`:
```ini
CONFIG_SENSOR=y
CONFIG_I2C=y
CONFIG_MAX17048=y
CONFIG_LOG=y
```