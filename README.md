### How to use the Easy UBNT (deprecated) script
You can run the script this way:
```console
wget https://raw.githubusercontent.com/sprockteam/ubi-tools/master/easy-ubnt.sh -O easy-ubnt.sh
sudo bash easy-ubnt.sh
```

### Script command-line useage
```console
  Note:
  This script currently requires root access.

  Usage:
  sudo bash easy-ubnt.sh [options]

  Options:
  -a          Accept and skip the license agreement screen
  -c [arg]    Specify a command to issue to a product, used with -p
              The script will execute the specified command only and then exit
              Currently supported commands:
              'get-installed-version' - Show currently installed package version
              'get-available-version' - Show latest available version number
              'get-available-download' - Show latest available download URL
              'archive-alerts' - Archive controller alerts for all sites
  -d [arg]    Specify the domain name (FQDN) to use in the script
  -f [arg]    Specify an option for the firewall setup
              If not specified, the firewall (UFW) will be enabled
              Currently supported options:
              'off' - Disable the firewall
              'skip' - Don't make any firewall changes
  -h          Show this help screen
  -i [arg]    Specify a UBNT product version to install, used with -p
              Currently supported syntax examples:
              '5.9.29', 'stable', '5.7'
              Can also use 'skip' to bypass any UBNT product changes
  -l [arg]    Specify an option for the Let's Encrypt setup
              Currently supported options:
              'skip' - Don't do any Let's Encrypt setup
  -p [arg]    Specify which UBNT product to administer
              Currently supported products:
              'unifi-controller' (default)
  -q          Run the script in quick mode, accepting all default answers
  -s [arg]    Specify an option for the SSH server setup
              Currently supported options:
              '<port>' - Specify a port number to use
              'off' - Disable SSH
              'skip' - Don't do anything with SSH
  -t          Bypass normal script execution and run tests
  -v          Enable verbose screen output
  -x          Enable script execution tracing
  -z          Bypass initial system checks, common fixes and updates
```

### Quick mode example
You can run the script this way to quickly deploy a server with a Let's Encrypt cert and a basic firewall:
```console
wget https://raw.githubusercontent.com/sprockteam/ubi-tools/master/easy-ubnt.sh -qO easy-ubnt.sh && sudo bash easy-ubnt.sh -aqd unifi.fqdn.com
```

### Script Logging
The last 10 logs are saved in `/var/log/easy-ubnt` and the latest script log is symlinked as `latest.log`:
```console
more /var/log/easy-ubnt/latest.log
```
