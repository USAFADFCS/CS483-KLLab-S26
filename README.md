# CS 483 — Keyboard Logger Lab (PEX)

Starter code for the Keyboard Logger practical exercise in CS 483
(Operating Systems), USAFA DFCS.

## Contents

| File              | Role                                                           |
|-------------------|----------------------------------------------------------------|
| `hello_printk.c`  | Starter kernel module (prints a banner on load / unload).      |
| `keyboard.c`      | **Reference only.** Contains the notifier callback and the    |
|                   | `notifier_block` handle students splice into `hello_printk.c`. |
| `Makefile`        | Builds `hello_printk.ko` against the running kernel's headers. |

## Build

```bash
sudo apt install -y build-essential linux-headers-$(uname -r)
make
```

Produces `hello_printk.ko`.

## Load / unload

```bash
sudo insmod hello_printk.ko
lsmod | grep hello_printk
sudo dmesg | tail -5
sudo rmmod hello_printk
```

## Full instructions

Follow the HTML writeup distributed via **Canvas Lesson 36** for the
complete walkthrough, platform-specific prep (Fusion/ARM and
Workstation/Intel), the TTY-vs-GUI gotcha, and submission
requirements.

## Authorized use only

A keylogger is dual-use. You are writing this code to understand how
kernel-level input capture works so you can recognize and defend
against it. Running this module on any system you do not own —
including DoD, academic, or shared machines — is a federal crime
under the Computer Fraud and Abuse Act and a violation of the Cadet
Honor Code. Build and run this code only inside your own VM.

## Coding standard

All `.c` files follow the USAFA DFCS C Programming Standard v3.0
(01 Feb 2024): comment header blocks, `@brief`/`@param`/`@return`
function headers, ≤100 char lines, 4-space indentation, and
`camelCase` for student-authored functions. Kernel API identifiers
(`module_init`, `register_keyboard_notifier`, etc.) retain their
Linux kernel spellings.
