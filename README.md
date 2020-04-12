thermal_daemon with DPTF hacks
==============================

This is a fork of [Intel's Thermal Daemon](https://github.com/intel/thermal_daemon), extended to make use of the adaptive performance policy implemented on many modern ultrabook designs. This is a very long way from complete, and may not work for you at all.

How to use it
-------------

You need a kernel that contains the patches in the patches directory. Once you have that, build thermal_daemon and run it as root with the ``--adaptive --exclusive-control`` arguments. It will attempt to parse your firmware's policy file. If you get an error, either your laptop doesn't implement this policy or you've run into a limitation of this implementation. Open an issue with the error output you get.

Todo
----

Add support for other conditions. At the moment, the only conditions supported are associated with OEM-specific variables. This is all my test machine uses, so adding others hasn't been a priority.

Add support for other targets. Right now this only supports loading a new passive table or modifying RAPL parameters. Again, this is all my test machine uses.

Add support for other table versions. I've implemented what I can based on what I've been able to find out, but if the table versions aren't what's expected, it'll definitely break at the moment.

Add support for the APPC table. The one on my laptop seems to be malformed, but isn't needed for the conditions it uses, so I don't know whether it's genuinely broken or whether I'm doing something wrong.

Get this merged into the mainstream implementation.

Note
----

This is, as should be obvious, very much not an official or supported Google project.