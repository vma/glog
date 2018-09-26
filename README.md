# glog

Leveled execution logs for Go.


## About

This package is forked from https://github.com/golang/glog with the following changes:

- The command line options are managed with getopt (github.com/vma/getopt) instead of flags

- All logs are stored in one file instead of one file per level

- Log file name is simplified and no symlinks are created

- Max log file size before rotation is configurable (`--logsize`)

- If `--logdir` is not set, the default log output is `stderr`

- The log filename and line are only displayed when `--location` is set (performance boost)

- The log line format is `[L] yyyy-mm-dd hh:mm:ss.uuuuuu file:line - msg...`

- A Logger wrapper was added to allow prefixed logging and per object logger

- All bridging code with default go log pkg was removed

- bugfix: use CallersFrames instead of FuncForPC to get the correct filename

- getopt.Parse() is called automatically if needed before the first output


## Installation

Installation can be done as usual:

```
$ go get github.com/vma/glog
```

## Usage

Basic examples:

```
glog.Info("Prepare to repel boarders")
glog.Warning("This is a warning")
glog.Fatalf("Initialization failed: %s", err)
```

See the documentation for the V function for an explanation of these examples:

```
if glog.V(2) {
    glog.Info("Starting transaction...")
}

glog.V(2).Info("Processed", nItems, "elements")
```
