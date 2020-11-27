.. _ug_tfm:

Implementing Trusted Firmware-M in your application
###################################################

.. contents::
   :local:
   :depth: 2

On nRF5340 and nRF9160, you can use Trusted Firmware-M (TF-M) as an alternative to :ref:`secure_partition_manager` for running an application from the non-secure area of the memory.

Overview
********

TF-M is the reference implementation of `Platform Security Architecture (PSA)`_.

It provides a highly configurable set of software components to create a Trusted Execution Environment.
This is achieved by a set of secure run time services such as Secure Storage, Cryptography, Audit Logs, and Attestation.
Additionally, secure boot via MCUboot in TF-M ensures integrity of run time software and supports firmware upgrade.

For official documentation, see `TF-M documentation`_.

TF-M implementation in |NCS| is currently demonstrated in the :ref:`tfm_hello_world` sample.

Building
********

To add TF-M to your build, enable the :option:`CONFIG_BUILD_WITH_TFM` config by adding it to your :file:`prj.conf` file.
:note: If you instead enable :option:`CONFIG_BUILD_WITH_TFM` via menuconfig, you must also enable its dependencies.
You must build with a nonsecure board. Currently these are supported:

 * nrf5340dk_nrf5340_cpuappns
 * nrf5340pdk_nrf5340_cpuappns
 * nrf9160dk_nrf9160ns

If you are using nrf9160dk_nrf9160ns, copy the .overlay file from tfm_hello_world to disable UART1 in the nonsecure app, since this UART is used by the TF-M secure app.

Programming
***********

In NCS, flashing an app with TF-M is done like other multi-image apps.
After building, a :file:`merged.hex` file is created which contains MCUboot, TF-M, and the app.
:file:`merged.hex` is flashed automatically when ninja flash or west flash is called.

Logging
*******

TF-M employs two UARTs for logging, one for secure (MCUboot and TF-M), and one for the nonsecure app.
These will arrive on different COM ports on the host PC.

On the nRF5340 DK/PDK, you must connect wires on the board to receive secure logs on the host PC.
Wire the pins P0.25 and P0.26 to RxD and TxD respectively.
