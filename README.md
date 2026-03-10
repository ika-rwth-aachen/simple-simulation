# simple-simulation

<img src="https://github.com/ika-rwth-aachen/simple-simulation/blob/main/simple-simulation.svg?raw=True" width="400px" style="margin: 10px;">



Execute simulation runs defined by [simple-scenario](https://github.com/ika-rwth-aachen/simple-scenario) to efficiently develop scenario-based testing methods (e.g., selecting test scenarios or testing prototype automated driving systems).

# Examples

:bulb: *To recreate these videos use: `examples/generate_simulation_run_videos.py`.*

## Free driving test scenario

`examples/example_scenario0.json`

Test scenario:

<img src="assets/example_scenario0.gif">

Simulation run:

<img src="assets/example_scenario0_simulation_run.gif">

Result: `is_goal_reached`

## Deceleration test scenario

`examples/example_scenario1.json`

Test scenario:

<img src="assets/example_scenario1.gif">

Simulation run:

<img src="assets/example_scenario1_simulation_run.gif">

Result: `is_standstill`

## Cut-in test scenario

`examples/example_scenario2.json`

Test scenario:

<img src="assets/example_scenario2.gif">

Simulation run:

<img src="assets/example_scenario2_simulation_run.gif">

Result: `is_collision`

# Notice

> [!IMPORTANT]
> This repository is open-sourced and maintained by the [**Institute for Automotive Engineering (ika) at RWTH Aachen University**](https://www.ika.rwth-aachen.de/).
> We cover a wide variety of research topics within our [*Vehicle Intelligence & Automated Driving*](https://www.ika.rwth-aachen.de/en/competences/fields-of-research/vehicle-intelligence-automated-driving.html) domain.
> If you would like to learn more about how we can support your automated driving or robotics efforts, feel free to reach out to us!
> :email: ***opensource@ika.rwth-aachen.de***


# Install

To use or develop `simple-simulation`, you must first clone the repository.

```bash
$ git clone git@github.com:ika-rwth-aachen/simple-simulation.git
$ cd simple-simulation
```

It is recommended to use [uv](https://docs.astral.sh/uv/getting-started/installation/) for package management. If you do not want to use `uv`, please consult the [Without uv](#without-uv) section.

## With uv

Install requirements with

```bash
$ uv sync
```

To run a script, use

```bash
$ uv run /path/to/script.py
```

or directly use the python interpreter from the `.venv` folder in e.g. VSCode.

To run the tests, install the dev requirements with

```bash
$ uv sync --dev
```

and run the tests

```bash
$ uv run pytest
```

## Without uv

Install the project editable

```bash
$ python -m pip install -e .
```

To run the tests, first install pytest

```bash
$ python -m pip install pytest
```

and run

```bash
$ pytest
```
# Use

:bulb: You should first complete the [Installation](#install).

Run some simulations

1. Open the file `test/test_challenger_a.py` and run it by clicking on the run arrow in the top right corner.

2. There should be some videos in the folder `test/test_results/challenger_a/`.

You can watch them directly in VSCode.

# Dev

The `simple_simulation` module consists of the following submodules:

* `simulation_manager/`: Main module handling all other modules to run the main simulation loop.
* `pilots/`: Pilots for the simulation actors. A pilot takes high-level decisions for lateral and longitudinal control for exactly one simulation actor based on the current situation in the simulation. Each pilot must be a subclass of `Pilot` in `pilots/pilot.py`. The logic contained in `highway_pilot.py` is roughly based on that of the [l3pilot-aeb-adf](https://github.com/l3pilot/l3pilot-aeb-adf).
* `simulation_core/`: The lightweight simulation core using [CommonRoad vehicle models](https://gitlab.lrz.de/tum-cps/commonroad-vehicle-models).

# Acknowledgements

This package is developed as part of the [Hi-Drive project](https://www.hi-drive.eu).

<!-- <img src="https://raw.githubusercontent.com/ika-rwth-aachen/simple-simulation/refs/heads/main/assets/Hi_Drive_Logo_Claim_rgb.svg" style="width:2in" /> -->
<img src="assets/Hi_Drive_Logo_Claim_rgb.svg" style="width:2in" />

The research leading to these results has received funding from the European Union’s Horizon 2020 research and innovation programme under grant agreement No 101006664.
The sole responsibility of this publication lies with the authors.
The authors would like to thank all partners within the Hi-Drive project (hi-drive.eu) for their cooperation and valuable contribution.

<!-- <img src="https://raw.githubusercontent.com/ika-rwth-aachen/simple-simulation/refs/heads/main/assets/funded_by_eu.svg" style="width:4in" /> -->
<img src="assets/funded_by_eu.svg" style="width:4in" />

Additional development is done within the [SYNERGIES project](https://synergies-ccam.eu/).

<img src="assets/synergies.svg" style="width:4in" />