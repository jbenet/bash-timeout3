# timeout3 - execute a command with a timeout

Execute a command with a time-out.
Upon time-out expiration `SIGTERM (15)` is sent to the process. If `SIGTERM`
signal is blocked, then a subsequent `SIGKILL (9)` terminates it.

## Install

Something like
```
git clone https://github.com/jbenet/bash-timeout3
mv bash-timeout3/timeout3-v2 /usr/bin/timeout3
```

## Usage

### Examples

```sh
# timeout $(sleep 10) at 5 seconds.
> ./timeout3-v1 -t 5 sleep 10
Terminated: 15
```

### v1

```
> ./timeout3-v1
Synopsis
    timeout3-v1 [-t timeout] [-i interval] [-d delay] command
    Execute a command with a time-out.
    Upon time-out expiration SIGTERM (15) is sent to the process. If SIGTERM
    signal is blocked, then the subsequent SIGKILL (9) terminates it.
    -t timeout
        Number of seconds to wait for command completion.
        Default value: 9 seconds.
    -i interval
        Interval between checks if the process is still alive.
        Positive integer, default value: 1 seconds.
    -d delay
        Delay between posting the SIGTERM signal and destroying the
        process by SIGKILL. Default value: 1 seconds.
As of today, Bash does not support floating point arithmetic (sleep does),
therefore all delay/time values must be integers.
```

### v2

```
> ./timeout-v2
Synopsis:  timeout3-v2 [-t timeout] [-i interval] [-d delay] command

Executes the command with a time-out.  Upon time-out expiration SIGTERM (15) is
sent to the process.  If SIGTERM signal is blocked, then the subsequent SIGKILL
(9) terminates it.

-t timeout
    Number of seconds to wait for command completion.
    Default value: 5 seconds.  In some practical situations
    this value must be increased (for instance -t 180) to allow
    the command to complete.

-i interval
    Interval between checks if the process is still alive.
    Positive integer, default value: 1 seconds.
    Default value is OK for most situations.

-d delay
    Delay between posting the SIGTERM signal and destroying the process by
    SIGKILL.  Default value: 1 seconds.
    Default value is OK for most situations.

As of today, Bash does not support floating point arithmetic (sleep does),
therefore all time values must be integers.
```

## History

This little script has a fun history:

- 2011: script contributed to bash by @golovashkin
- 2011: cleaned up by Chet
- 2013: removed from bash at the request of FSF
- 2016: MIT Licensed by @golovashkin at the request of @jbenet

See version histories at:
- http://git.savannah.gnu.org/cgit/bash.git/log/examples/scripts/timeout3?h=bash-4.3-testing
- http://github.com/jbenet/bash-timeout3

## License

MIT
