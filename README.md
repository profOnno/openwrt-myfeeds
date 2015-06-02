# openwrt-myfeeds

I'm a noob, but got to start somewhere..
This feed for openwrt contains jq. There is a patch included that strips `y0`,`y1`,`j0`,`j1` from `libm.h`. That means no bessel functions (i don't think i'll miss it).

If you've downloaded and setup a openwrt buildsystem. Add src-git myfeeds https://github.com/profOnno/openwrt-myfeeds.git to the feeds.conf.default. Do a `scripts/feeds update myfeeds` en then `scripts/feeds install jq` if you want to install jq. Then, when you do a `make menuconfig`, jq can be found in the utilities.

I'm planning to use jq ncat (the one in the Network/NMAP menu, for unix sockets) and bash to work in Docker using a openwrt image.
So you can do : `echo -e "GET /containers/json HTTP/1.0\r\n" | nc -U /var/run/docker.sock | sed -e '1,/^\r$/d' |jq .`
The `sed` part removes the header, `jq` gives a nice output.

To show the first name of each container.
 `echo -e "GET /containers/json HTTP/1.0\r\n" | nc -U /var/run/docker.sock | sed -e '1,/^\r$/d' |jq '.[] |.Names[0]'`
 
 Fancy..
 `echo -e "GET /containers/json HTTP/1.0\r\n" | nc -U /var/run/docker.sock | sed -e '1,/^\r$/d' |jq '.[] |"\(.Names[0]), \(.Status)"'`
 
