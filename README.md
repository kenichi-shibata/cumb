# This is for research purposes only.
## Do not use this software for illegal or unauthorized uses.

# cumb
Umbrella Client Controller for Mac OSX written in Bash and Launchctl

## Installation

```
git clone git@github.com:kenichi-shibata/cumb.git cumb
chmod +x cumb/bin/cumb
export PATH=${PWD}/bin:${PATH} 
```

If you want to persist this you may want to add this to `PATH` in `zshrc` or `bashrc`. 
## Usage

> **NOTE**: you need admin permissions to run this on you macOS

```
Usage: cumb COMMAND
  COMMANDS:
    stop    Run sudo launchctl unload /Library/LaunchDaemons/com.opendns.osx.RoamingClientConfigUpdater.plist
    start   Run sudo launchctl load /Library/LaunchDaemons/com.opendns.osx.RoamingClientConfigUpdater.plist
    restart Stop umbrella, then start again.
    list    Check all PIDs if they are running using launchctl
    dig     Check OpenDNS records txt, if you can dig it, it means you are behind umbrella client and OpenDNS
    cat     Print the Config files,
    edit    Update this function, hardcoded with Kenichi's setup does not work outside that
    status  Is umbrella running?
```

**status**
```
❯ cumb status
Umbrella is running. Checking debug.opendns.com DNS…
debug.opendns.com.	0	IN	TXT	"server r5.lon"
debug.opendns.com.	0	IN	TXT	"device 010182cb7cb0be0c"
debug.opendns.com.	0	IN	TXT	"remoteip 192.168.1.180"
debug.opendns.com.	0	IN	TXT	"flags 40034 0 186040 1E10000074060000060039F0400FE2080081681"
debug.opendns.com.	0	IN	TXT	"originid 472625284"
debug.opendns.com.	0	IN	TXT	"orgid 2353377"
debug.opendns.com.	0	IN	TXT	"orgflags 100A6"
debug.opendns.com.	0	IN	TXT	"actype 0"
debug.opendns.com.	0	IN	TXT	"bundle 6892016"
debug.opendns.com.	0	IN	TXT	"source 95.149.61.43:61225"
debug.opendns.com.	0	IN	TXT	"dnscrypt enabled (716A7A6D6D486A53)"
Currently using name servers:
```

**stop**
```
❯ cumb stop
Password:
Umbrella is stopped
Currently using name servers:
❯ cumb status
Umbrella is stopped
Currently using name servers:
```

**start**

```
❯ cumb start
/Library/LaunchAgents/com.opendns.osx.RoamingClientMenubar.plist: No such file or directory
/Library/LaunchAgents/com.cisco.umbrella.menu.plist: service already loaded
Umbrella is running. Checking debug.opendns.com DNS…
Umbrella is not functioning correctly!
Currently using name servers:

sleep 30

❯ cumb status
Umbrella is running. Checking debug.opendns.com DNS…
debug.opendns.com.	0	IN	TXT	"server r5.lon"
debug.opendns.com.	0	IN	TXT	"device 010182cb7cb0be0c"
debug.opendns.com.	0	IN	TXT	"remoteip 192.168.1.180"
debug.opendns.com.	0	IN	TXT	"flags 40034 0 186040 1E10000074060000060039F0400FE2080081681"
debug.opendns.com.	0	IN	TXT	"originid 472625284"
debug.opendns.com.	0	IN	TXT	"orgid 2353377"
debug.opendns.com.	0	IN	TXT	"orgflags 100A6"
debug.opendns.com.	0	IN	TXT	"actype 0"
debug.opendns.com.	0	IN	TXT	"bundle 6892016"
debug.opendns.com.	0	IN	TXT	"source 95.149.61.43:61225"
debug.opendns.com.	0	IN	TXT	"dnscrypt enabled (716A7A6D6D486A53)"
Currently using name servers:
```

Start up of Umbrella Client takes between 1-4 mins. On the meanwhile you can use `cumb status` to check once its up and running.
