# Command line tool for automating customization and configuration of handhelds & PCs running SteamOS

## Enabling Linux Dynamic Kernel Module Support ACPI calls

In order to enable custom fan curves and setting the Legion Go charge limit we need to enable
DKMS ACPI call support for SteamOS. Note that this tool can be used to enable DKMS on any
handheld or gaming PC running SteamOS.

In order to enable the ACPI calls the following needs to happen:

- Disable SteamOS read-only mode
- Download and install the required kernel moduels and kernel header packages
- Install the packages that enable the various daemons require for ACPI calls
- Re-enable SteamOS read-only mode

This script automates all of the above with a single command.

The command is as follows:

```
./SteamOsUtils.py --enable_acpi_calls
```

The command will take several minutes to run depending on your internect connection.

Once the above command is complete you should see a log like this in the console:

```
Congratulation! You now can enable custom fan curves and control charge limit!
```

We can confirm that the DKMS ACPI support is enabled by running the following command:

```
dkms status
```

If the DKMS ACPI was successfully enabled we should see an output similar to this:

```
acpi_call/1.2.2, 6.11.11-valve24-2-neptune-611-gfd0dd251480d, x86_64: installed
```

# Note
When I started this project I wanted to have it work for a small list of kernel versions that I could test locally before opening it up to all versions.

This was done by design so I wouldn't get a ton of tickets, while watching to see how well the tool will run in the wild.

This set of tools was originally made for and tested on the Legion Go, but it works on all
computing devices that run SteamOS.

Currently I am testing new features with my SteamOS powered high-performance gaming PCs.
