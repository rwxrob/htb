# OpenVPN Files

Even though they are ignored with the following `.gitignore` this is
where I keep the different `*.opvn` files required by HackTheBox.

```gitignore
*
*/
!.gitignore
!README.md
```
Use the following from a dedicated TMUX window (named `VPN`) to start
the required VPN:

```
sudo openvpn FILE.ovpn
```
