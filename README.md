# TB6612FNG

Drive for the TB6612FNG Motor Driver module, available from [Sparkfun](https://www.sparkfun.com/products/14451) and other sources.

Refer to the [Data Sheet](https://www.sparkfun.com/datasheets/Robotics/TB6612FNG.pdf) for more detail.

## Installation

Add  `tb6612fng` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [
    {:tb6612fng, "~> 0.1.0"}
  ]
end
```

## Usage

Add one or more `TB6612FNG` supervisors to your supervision tree.  Each instance of `TB6612FNG` can be configured to handle two motors.

```elixir
{TB6612FNG, [
        standby_pin: 21,
        motor_a: [
          pwm_pin: 12,
          in01_pin: 20,
          in02_pin: 16,
          name: :motor_a
        ],
        motor_b: [
          pwm_pin: 13,
          in01_pin: 5,
          in02_pin: 6,
          name: :motor_b
        ]
       name: :my_tb6612fng_module # defaults to __MODULE__
      ]}
```

Then control the motors as necessary from TB6612FNG.Module

```elixir
TB6612FNG.Module.set_output(:motor_a, :cw, 100_000)
```

