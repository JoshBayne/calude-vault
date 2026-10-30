## How to connect to Cisco device? 
### Console Port
Rollover cable, RJ45 on one end to Blue Console 
Pinout
	1 to 8
	2 to 7
	3 to 6
	4 to 5

Access CLI with terminal emulator like PuTTy
settings:
	Speed (baud) 9600
	8 data bits
	1 stop bit
	parity - none
	flow control - none

## User EXEC Mode
denoted on cli with `hostname>`
`/>` means user exe mode
very limited
cant make any changes to config, basically user mode

## Privileged EXEC Mode
if you enter the `enable` command you will enter privileged mode
denoted with # ex `hostname#`
provides complete access to config files
cannot change config but can change some settings

## Global config mode
`configure terminal` is the command to enter this mode
can be shortened to `conf t`
denoted by `hostname(config)#`

## Enable Password
`enable password LINE` to add password
passwords are case sensitive
3 attempts to login

2 seperate config files
running-config - running current config. 
startup-config - config file thats loaded on boot.

`show running-config` command to view file
`show startup-config` command to view file

3 ways to save running to startup using priv exec mode
`write`
`write memory`
`copy running-config startup-config`

`service password-encryption` to encrypt password from being shown in clear text
stil not the most secure, can be cracked using crackers online
`enable secret`  for MD5 encryption on password
secret supercedes password command

`do` acts like `sudo`

`no` in front of command to cancel a command
ex. `no service password-encryption` means any new passwords will not be encrypted anymore

