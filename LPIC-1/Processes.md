# Processes
pid 1       init or systmed  
pid 2       kthreadd  kernel threads  :w


All other processes are child processes

## ps
ps gets its info from the /proc directory  

    ps
    ps -u <username>
    ps -e               # every process from all users
    ps -H               # show process hierarchy
    ps --forest
    ps -f               # full format listing

## top
real time monitoring of processes  
While in `top`, press `k` and you will be prompted for a pid to kill


## Monitoring

    uptime          # load avg for last 1min, 5min, 15min
                    # 1.0 w 1 cpu means 100% load
                    # 1.0 w 4 CPUs means 25% load

    free            # used and available memory, also shows swap space
    free -m         # display megabytes
    free -g         # display gigabytes
    free -h         # human readable

## pgrep
like `ps` but for processes. Can search by 'name' or 'pid'. 

    pgrep httpd         # only lists pids
    pgrep  -a httpd     # shows all info 
    pgrep -u <user>     # show all processes of a user

## Signals
man 7 signal  
search for 'Standard signals'
- SIGHUP    1
- SIGKILL   9       # pull plug. may leave files and stale processes
- SIGTERM   15      # graceful termimation. removes files and child processes

### commands

    kill <pid>      # send SIGTERM based on pid
    kill -l         # list signals you can pass to the kill command
    kill -9 <pid>   # send SIGKILL for the pid
    pkill <name>    # SIGTERM based on process name
    pkill -x <name> # only kill the the exact process name
    killall <name>  # kill all process associated with the name
    killall -s 9 <name>  # SIGKILL all process associated with the name

## Watch
Monitor the output of a command  
the command will be re-run periodically

    watch date
    watch  -n 5 date    # update every 5 seconds

## screen

    screen
    Ctrl-a  d       # detach
    screen -r       # re-attach
    screen -r <id>  # re-attach with screen id
    exit
    screen -ls      # list running screen sessions

## tmux

    tmux
    ctrl-b  d
    tmux ls
    tmux attach-session -t 0
    exit

## Keep a process running

    nohup ping 10.1.1.12 &          # gets signal 1 (HOHUP) 
                                    # & send the process to the background
                                    # the process will continue if the terminal closes
                                    # as long as the login session does not end

    jobs                            # list processes running in the backbround
    jobs -l                         # list processes with pid
    tail -f nohup.out               # to see the output of the command
    fg 2                            # bring to foreground job number 2
    ctrl-z                          # send to background and pause the process
    bg %2                           # send to background and keep running
    kill <pid>                      # to stop a process running in the background


## Process Priorities
Process priority called `nice level`  
Ranges

    -20     highest
     19     Lowest
      0     default for most process

Can change the priority of a process  
- only root can 'lower' the `nice level`
- anyone can 'raise' the `nice level` of a process they own

commands

    ps -o pid,nice,cmd,user         # output specific fields
    nice -n 5 <cmd>                 # run a process at a specific nice level
    renice -n 1 <pid>               # change nice level of a running process
    top - r - pid - nice level      # renice using top


