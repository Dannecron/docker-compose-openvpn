# docker-compose-openvpn

Based on [kylemanna/docker-openvpn](https://github.com/kylemanna/docker-openvpn)

## Screencast on YouTube

You can see this repo in action (from 4:16 to 6:10).

[![](http://i3.ytimg.com/vi/KApzBc6V6HY/maxresdefault.jpg)](http://www.youtube.com/watch?v=KApzBc6V6HY "")


## Start


### Generate configs

Run

```
make genconfig host=vpn.example.com
```

And then

```
make initpki
```

*Please save entered password. You'll need it for certificate management.*


### Generate new cert

```
make new username=example
```

Copy client_configs/example.ovpn to your local machine and use them in OpenVPN client.

__Note:__ if your openvpn client version is `2.3.x`, then you must add a new line with `comp-lzo no` to the first paragraph of `client_configs/example.ovpn` (before `remote` definition).
Overwise there will be errors `Bad compression stub decompression header` on server side and no connection to internet from client.

### Start VPN server

```
make up
```

## Additional management commands

### Stop VPN server

```
make stop
```

### View the status

```
make ps
```

### Revoke cert

```
make revoke username=example
```
