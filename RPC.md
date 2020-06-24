# RPC Cheatsheet
## Access
### Logging in without a user
`rpcclient (IP)`
### Logging in as a blank user
`rpcclient -U '' (IP)`

Often enabled on older insecured DNS servers

## `enumdomusers`
Lists all users
### Trim output nicely with
`cat (enumdomusers output) | awk -F\[ 'print $2}' | awk -F\] '{print $1}' > (output filename)`
## `queryuser 0x(user number)`
Lists info about user
## `enumdomgroups`
Lists all groups
## `querygroup 0x(group number)`
Lists info about group
## `querygroupmem 0x(group number)`
Lists group members
## More details
In RPC client, run `querdispinfo`
