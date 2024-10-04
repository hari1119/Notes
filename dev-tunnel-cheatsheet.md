### Devtunnel
- Devtunnel is used to forward the port to the pubile, using the git hub account,
  it's opensource developed by the microsoft.

###### Install

```
curl -sL https://aka.ms/DevTunnelCliInstall | bash
```

then,

```
source ~/.bashrc
```

To check the installed  status

```
devtunnel --version
```

```
devtunnel -h
```
To Login into the devtunnel

```
devtunnel login -d
```
 - once u excute the above command, u will get the link and code
 - copy the code and entry in the give link
 - then login with the microsoft account
Create a devtunnel
 - Once all the above things all done.
 - follow the below command to create the devtunnel.
```
devtunnel create <tunnel-name>
```
Port Forwarding to public link.
```
devtunnel host -p 8021 --allow-anonymous
```
- use the above command to forward the local port to public link.
- Once the devtunnel run successfully, we able to get the public link.
   
