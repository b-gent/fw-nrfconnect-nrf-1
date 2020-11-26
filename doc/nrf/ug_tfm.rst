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
Additionally, secure boot in TF-M ensures integrity of run time software and supports firmware upgrade.

For official documentation, see `TF-M documentation`_.

TF-M implementation in |NCS| is currently demonstrated in the :ref:`tfm_hello_world` sample.


---> More content needed about how exactly this is done. Something like http://developer.nordicsemi.com/nRF_Connect_SDK/doc/latest/nrf/include/spm.html can be a good starting point.
