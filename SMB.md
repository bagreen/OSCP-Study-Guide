# SMB Cheatsheet
## Find interesting files
`crackampexec smb (IP)`

## Finding shares
### Anonymous access
`smbclient -L //(IP)`

`smbclient -U '' -L //(IP)`

`crackmapexec smb (IP) --shares`

### Common User Accounts
`smbclient -U 'anonymous' -L //(IP)`

`smbclient -U 'guest' -L //(IP)`

## Find password policy
`crackmapexec smb (IP) --pass-pol`

## Mount SMB shares in Linux so that you can use Linux commands for searching files
`sudo mount -t cifs -o 'username=(username).password=(password)' //(IP) /(mountpoint)`

## Find a user's accessible shares
`smbmap -U (username) -p (password) -H (IP)`
