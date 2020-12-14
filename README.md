# Assumed Setup
- deluge running in a docker container
- Filebot installed and registered
- podman installed

# Installation Instructions
After installing requirements with pip, just run ./install which will copy all files and create the systemd service
~~~
pip3 install -r requirements
./install
systemctl enable --now autobot
~~~

# To run locally:
Install Requirements with pip:
~~~
pip3 install -r requirements
~~~
copy autobot.yml from ./lib and edit to suit.
~~~
cp lib/autobot.yml autobot.yml
vi autobot.yml
~~~
Then run ./autobot to manage media.
~~~
./autobot
~~~

## Usage:
~~~
autobot [-c CONFIG_FILE] [-s]
~~~
-c    Specify config file
-s    Run as a service

# Editing the Config File
Order of precedence: CLI Argument > autobot.yml in current directory > .autobot.yml in HOME > /etc/autobot/autobot.yml
## Example Config
~~~
loglevel: DEBUG, INFO, WARN, ERROR
logfile: /path/to/log
unknown_files: /path/to/move/failed/files

rules:
- name    : Rule Name
  type    : fbmove, fbcopy, copy
  dir     : /path/to/scan/for/files
  pattern : '/path/to/output/with/filebot/pattern'
  database: filebot database
  enabled : true
  ~~~
  
  Types:
  - fbmove  Rename and move files with FileBot
  - fbcopy  Copy media files and rename to new location - will add a *.nocopy* file to hide from future scans.  Useful for seeding.
  - copy    Direct copy using cp.  Useful for seeding and managing files outside of filebot
  
  Patterns: See [FileBot's Documentation](https://www.filebot.net/naming.html) on expressions
  
  # ToDo
  - Create 'finish' variable in config to run commands for each file after processing
  - Move deluge control code to its own script to work with 'finish'
