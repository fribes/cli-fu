`sudo !!`
Run the last command as root
Useful when you forget to use sudo for a command. "!!" grabs the last run command.

------------------------------------

`python -m SimpleHTTPServer`
Serve current directory tree at http://$HOSTNAME:8000/

------------------------------------

`^foo^bar`
Runs previous command but replacing

Really useful for when you have a typo in a previous command. Also, arguments default to empty so if you accidentally run:
echo "no typozs"

you can correct it with
^z

------------------------------------

`ctrl-x e`
Rapidly invoke an editor to write a long, complex, or tricky command

Next time you are using your shell, try typing ctrl-x e (that is holding control key press x and then e). The shell will take what you've written on the command line thus far and paste it into the editor specified by $EDITOR. Then you can edit at leisure using all the powerful macros and commands of vi, emacs, nano, or whatever.

------------------------------------

`'ALT+.' or '<ESC> .'`
Place the argument of the most recent command on the shell

When typing out long arguments, such as:
cp file.txt /var/www/wp-content/uploads/2009/03/
You can put that argument on your command line by holding down the ALT key and pressing the period '.' or by pressing <ESC> then the period '.'. For example:
cd 'ALT+.'
would put '/var/www/wp-content/uploads/2009/03/ as my argument. Keeping pressing 'ALT+.' to cycle through arguments of your commands starting from most recent to oldest. This can save a ton of typing.

------------------------------------

`reset`
Salvage a borked terminal

If you bork your terminal by sending binary data to STDOUT or similar, you can get your terminal back using this command rather than killing and restarting the session. Note that you often won't be able to see the characters as you type them.

------------------------------------

`mount | column -t`
currently mounted filesystems in nice layout

Particularly useful if you're mounting different drives, using the following command will allow you to see all the filesystems currently mounted on your computer and their respective specs with the added benefit of nice formatting.

------------------------------------

`echo "ls -l" | at midnight`
Execute a command at a given time

This is an alternative to cron which allows a one-off task to be scheduled for a certain time.

------------------------------------

`curl ifconfig.me`
Get your external IP address

curl ifconfig.me/ip -> IP Adress

curl ifconfig.me/host -> Remote Host

curl ifconfig.me/ua ->User Agent

curl ifconfig.me/port -> Port

thonks to http://ifconfig.me/

------------------------------------

`man ascii`
Quick access to the ascii table.

------------------------------------

`dig +short txt <keyword>.wp.dg.cx`
Query Wikipedia via console over DNS

Query Wikipedia by issuing a DNS query for a TXT record. The TXT record will also include a short URL to the complete corresponding Wikipedia entry.You can also write a little shell script like:
$ cat wikisole.sh

#!/bin/sh

dig +short txt ${1}.wp.dg.cx

and run it like
./wikisole.sh unix

were your first option ($1) will be used as search term.

------------------------------------

`dd if=/dev/dsp | ssh -c arcfour -C username@host dd of=/dev/dsp`
output your microphone to a remote computer's speaker

This will output the sound from your microphone port to the ssh target computer's speaker port. The sound quality is very bad, so you will hear a lot of hissing.

------------------------------------

`<ctrl+u> [...] <ctrl+y>`
type partial command, kill this command, check something you forgot, yank the command, resume typing.

Example :
vim /etc/fstab

## damn
<ctrl+u> sudo <ctrl+y>

## like a boss.

Example 2 :
sudo vim /root/bin/

##uh... autocomplete doesn't work...
<ctrl+u> sudo ls /root/bin

##ah! that's the name of the file!
<ctrl+y> sudo vim /root/bin/ ##resume here! Thanks readline!

------------------------------------

`sshfs name@server:/path/to/folder /path/to/mount/point`
Mount folder/filesystem through SSH

Install SSHFS from http://fuse.sourceforge.net/sshfs.html

Will allow you to mount a folder security over a network.

------------------------------------

`mount -t tmpfs tmpfs /mnt -o size=1024m`
Mount a temporary ram partition

Makes a partition in ram which is useful if you need a temporary working space as read/write access is fast.

Be aware that anything saved in this partition will be gone after your computer is turned off.


------------------------------------
`wget --random-wait -r -p -e robots=off -U mozilla http://www.example.com`
Download an entire website

-p parameter tells wget to include all files, including images.

-e robots=off you don't want wget to obey by the robots.txt file

-U mozilla as your browsers identity.

--random-wait to let wget chose a random number of seconds to wait, avoid get into black list.

Other Useful wget Parameters:

--limit-rate=20k limits the rate at which it downloads files.

-b continues wget after logging out.

-o $HOME/wget_log.txt logs the output

------------------------------------

`ctrl-l`
Clear the terminal screen

------------------------------------

`curl -u user:pass -d status="Tweeting from the shell" http://twitter.com/statuses/update.xml`
Update twitter via curl

------------------------------------

`ssh user@host cat /path/to/remotefile | diff /path/to/localfile -`
Compare a remote file with a local file

Useful for checking if there are differences between local and remote files.

------------------------------------

`time read (ctrl-d to stop)`
A very simple and useful stopwatch

time read -sn1 (s:silent, n:number of characters. Press any character to stop)

------------------------------------

`ssh -t reachable_host ssh unreachable_host`
SSH connection through host in the middle

Unreachable_host is unavailable from local network, but it's available from reachable_host's network. This command creates a connection to unreachable_host through "hidden" connection to reachable_host.

------------------------------------

`less +F somelogfile`
Make 'less' behave like 'tail -f'.

Using +F will put less in follow mode. This works similar to 'tail -f'. To stop scrolling, use the interrupt. Then you'll get the normal benefits of less (scroll, etc.).

Pressing SHIFT-F will resume the 'tailling'.

------------------------------------

`telnet towel.blinkenlights.nl`
Watch Star Wars via telnet

Use Ctrl-] to stop it.

------------------------------------

`disown -a && exit`
Close shell keeping all subprocess running

while sleep 1;do tput sc;tput cup 0 $(($(tput cols)-29));date;tput rc;done &
Put a console clock in top right corner

A nice way to use the console in full screen without forget the current time.

you can too add other infos like cpu and mem use.
