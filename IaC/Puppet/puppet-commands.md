# Puppet Commands

### FACTER

| Command | Description |
| ------- | ----------- |
| `facter` | show all facters |
| `facter osfamily` | show OS Family facter |
| `facter -y` | show facters in YAML|
| `facter -j` | show facters in JSON |
| `notify { "OS is ${::facts['operatingsystem']}": }` | use fact inside a manifest using 'facter' function |
| `notify { "OS is $::operatingsystem": }` | use fact inside manifest directly |
| `$::operatingsystemmajrelease` | get OS major release from manifest |

### PUPPET AGENT

| Command | Description |
| ------- | ----------- |
| `puppet agent --test (or -t)` |Apply catalog using -verbose, -ignorecache, -no-daemonize -detailed-exit-codes, -show_diff |
| `puppet agent -t --debug` |Run in debug mode with more output |
| `puppet agent -t --noop ` | Run simulation (no changes to system)|
| `puppet agent -t --environment development` | Run catalog for different environment than whats configured in Puppet Agent's conf file |
| `puppet agent --disable` | Disable puppet agent from running on node|
| `puppet agent --enable` | Enable puppet agent to run on node |
| `puppet resource package` | show all installed packages |
| `puppet resource package apache ensure=present/absent` | install or remove package |
| `puppet resource` | show all managed resources |
| `puppet agent -t --graph` |show a graph of all dependencies found in a catalog, stored in a .dot image |

### Mcollective

| Command | Description |
| ------- | ----------- |
| `sudo -i -u peadmin` |Run MCollective as 'peadmin'|
| `mco ping` |check connection to nodes |
| `mco facts timezone` |get nodes by Facter name|
| `mco puppet count` |check how many MCO nodes are running|
| `mco rpc service restart service=httpd` | restart apache service|
| `mco package status puppet` | check status of a package |
| `mco inventory ––list-collectives` | list all subcollectives |
| `mco puppet disable -I nodename` |disable puppet agent on node |
| `mco ping -F architecture=x86_64` | find all nodes that are x64 |
| `mco find ––with-identity /nyc/` |find all nodes containing NYC in hostname |
| `mco find ––with-class nginx` |find all nodes with nginx class|
| `mco puppet runall -F osfamily=Redhat 5` |kick off 'puppet agent -t' on your nodes |
| `mco ping -T us_collective` |run command against a subcollective |
| `mco service ntp start -I ny14.nyc` |start/stop service on a node |
| `mco plugin doc` |show all available MCO plugins |
| `mco rpc puppet last_run_summary` |show last run statistics for all nodes |
| `/var/lib/peadmin/.mcollective.d/client.log` |mco client logs (on PE Master) |
