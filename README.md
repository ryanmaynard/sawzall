# Sawzall

Simple tool to hangle SSH config files. 

## Usage

To find the names of host definitions:

```
$ sawzall hosts
myremotehost
*
anothercloudbox
```

To return a definition for a single host: 

```
$ sawzall get myremotehost
Host myremotehost
	HostName 127.0.0.1
	Port 22
	User ryan
	IdentityFile %d/.ssh/rsa_key

```

Further, you can convert the definition to JSON with the `-j` option:

```
$ sawzall get -j myremotehost
{
  "HostName" "127.0.0.1",
  "Port" "22",
  "User" "ryan",
  "IdentityFile" "%d/.ssh/rsa_key"
}
```

For a more granular peek through your host definitions you can use `sawzall find`:

```

$ sawzall find rsa
Host myremotehost
  HostName 127.0.0.1
  Port 22
  User ryan
  IdentityFile %d/.ssh/rsa_key

Host *
  IdentityFile %d/.ssh/the_other_rsa_key

```

To copy a host definition onto a remote host: 

```
$ sawzall copy anothercloudbox user@myremotehost:9999
... ssh session follows ...

```