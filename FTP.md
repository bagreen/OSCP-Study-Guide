# FTP

## Check for anonymous access
`ftp (IP)` when asked for username, enter `anonymous`

## nmap scripts
`nmap -sV -Pn -vv -p21 --script=ftp-anon,ftp-bounce,ftp-libopie,ftp-proftpd-backdoor,ftp-vsftpd-backdoor,ftp-vuln-cve2010-4221`
