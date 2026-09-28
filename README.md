# Windows Server VM Recovery & Troubleshooting

## Overview

While completing a Windows Server/Active Directory lab using UTM, my
virtual machine unexpectedly booted into the Windows Server installation
process instead of loading my existing Windows Server environment.

This initially made it appear that the work completed during the lab had
been lost.

## Problem

The VM was booting from the Windows Server installation ISO rather than
the existing virtual hard disk containing the Windows Server environment.

## Investigation

I inspected the VM's storage configuration in UTM and identified three
attached drives:

- Windows Server ARM64 ISO - installation media
- UTM Guest Tools ISO
- `.qcow2` NVMe virtual disk - existing virtual hard drive

The `.qcow2` disk was still attached to the VM, indicating that the
existing Windows Server environment had not necessarily been erased.

## Resolution

I removed the Windows Server installation ISO from the VM's active drive
configuration while preserving the existing `.qcow2` virtual disk.

After restarting the VM, Windows Server successfully booted from the
existing virtual disk and the previously completed lab work was recovered.

## Skills Demonstrated

- UTM virtualization
- Windows Server troubleshooting
- Virtual disk identification
- Boot device troubleshooting
- ISO and virtual disk management
- System recovery
- Risk-aware troubleshooting
- Problem diagnosis

## Key Takeaway

This experience reinforced the importance of identifying the source of a
virtual machine boot problem before reinstalling an operating system or
modifying existing virtual disks. Preserving the original virtual disk
allowed the existing environment and lab work to be recovered without
rebuilding the server.

