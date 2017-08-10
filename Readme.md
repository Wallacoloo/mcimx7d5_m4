System View Description implementation for the M4 microcontroller embedded in the NXP i.mx7d5 SOC.

# Building
If all you want to do is interact with system registers in rust, just add this crate as a dependency to your project.

If you wish to edit the SVD file and generate a new register map (or reproduce this crate for another MCU), then the following process applies:

First, obtain your SVD file. These often come in a large CMSIS package. For example, the i.mx7d5 SVD was obtained
by downloading the "Device Family Pack" from [Keil](http://www.keil.com/dd2/nxp/mcimx7d5/), renaming the download to end in ".zip",
and then extracting the zip file and looking inside the SVD folder.

```sh
$ cargo install rustfmt svd2rust
# Note: Add ~/.cargo/bin to the PATH if necessary
$ svd2rust -i MCIMX7D5_M4.svd --target cortex-m | rustfmt > src/lib.rs
```

# License
Everything here is public domain, though users should consider that the original SVD file from NXP might be licensed differently
and that such a license probably applies to this derivative work.
