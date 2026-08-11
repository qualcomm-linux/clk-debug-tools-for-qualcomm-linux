# clk-debug-tools-for-qualcomm-linux

This project hosts out-of-tree Linux kernel clk debug patches for linux-next, plus scripts that drive clock-measurement based debugging on Qualcomm SoCs. It exposes hardware clock-measure support via debugfs so the actual measured rate of a clock can be checked against rate configured.

## Branches

**main**: Primary development branch.

## Requirements

- A `linux-next` kernel checkout for your target, with the DebugCC clk
  debug patches from `patches/` applied and built/flashed to the target.
- `debugfs` mounted on the target (`/sys/kernel/debug`).
- Root shell access on the target device.
- A POSIX shell (`sh`) on-target to run the helper scripts in `scripts/`.

List requirements to run the project, how to install them, instructions to use docker container, etc...

## Installation Instructions

1. Apply the patch series in `patches/` to a matching `linux-next`
   checkout for your target:

   ```sh
   # from a linux-next checkout
   git am /path/to/clk-debug-tools-for-qualcomm-linux/patches/*.patch
   ```

2. Build and flash the kernel to your target as usual.
3. Copy the scripts in `scripts/` onto the target

## Usage

**Using a helper script (SA8775P example):**

```sh
sh scripts/clk_measure_sa8775p.sh <clock_name>
```

**Notes:**

- `<clock_name>` must be present in the script's internal clocks list.
- Output is the measured clock rate in Hz.

