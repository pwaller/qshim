# qshim

A shim for `qsub` so that you can pass arguments directly to your job.

`torque-client-2.3.6` appears not to support this so qshim to the rescue!

Also supports running arbitrary binaries, not just scripts.

Example usage:

```
qshim ./myscript.py arg1 arg2 "arg3 with spaces"
```

Notes:

* Executes `qsub` for you
* Puts arguments into the environment as `QSHIM_ARG_N`
* qshim executes itself on the batch cluster with no arguments and then
  `exec()`'s into the desired script
* Merges stdout/stderr
* Passes whole environment to the target batch job
* Batch job runs in `$PWD` at time of submission
* Assumes that the `qshim` script is in your path

Pull requests welcome.

