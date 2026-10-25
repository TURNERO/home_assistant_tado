# home_assistant_tado
For Home Assistant and Tado

## Tado temperature offset blueprint

`tado_temp_offset.yaml` calibrates a Tado radiator thermostat to a separate room temperature sensor by adjusting its offset through Tado Hijack. It corrects part of the error per step and waits for Tado to report a new temperature before correcting again.

### Install
Copy the file to `<config>/blueprints/automation/<your-folder>/tado_temp_offset.yaml`, then create one automation per room.

### Inputs
- Reference temperature sensor
- Tado climate entity (HomeKit)
- Offset storage (optional `input_number`, min -9.9, max 10, step 0.1; if empty the offset number's state is used)
- Gain, deadband, maximum step, persistence and settle timeout

The Hijack offset entity is derived from the climate entity: `climate.X` becomes `number.X_temperature_offset`. The climate picker filters on the `homekit_controller` integration. If it is empty, remove the `integration:` line for that input in the blueprint.
