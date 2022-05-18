# NordVPN for Docker

Docker container based on NordVPN's example Dockerfile.

## Files

| File                | Description                          |
|---------------------|--------------------------------------|
| README.md           | The file that you're reading now.    |
| LICENSE.md          | MIT License text.                    |
| ubuntu/Dockerfile   | Container configuration.             |
| alpine/Dockerfile   | Experimental. (Not working yet.)     |
| .env                | Your NordAccount credentials.        |
| Vagrantfile         | Example VM configuration. (optional) |
| bin/start-vm        | Example VM start-up script.          |
| bin/start-container | Example container start-up script.   |

## Build and Run Container

* Build the image (tagged with the name, "nordvpn")

```
    docker build -t nordvpn .
```

* Run the container

```
    # attached to terminal
    docker run -it --cap-add=NET_ADMIN --device=/dev/net/tun nordvpn

    # or detached
    CID=$(docker run -d --cap-add=NET_ADMIN --device=/dev/net/tun nordvpn)
```

## NordAccount Credentials

You can save your NordAccount credentials in `.env`.

Example:
```
NORDACCOUNT_USERNAME=norduser@example.com
NORDACCOUNT_PASSWORD=XEt_vCjC5uECg@Pw
```

## Executing NordVPN Commands

Login to NordVPN
```
    docker exec $CID nordvpn login --username "$NORDACCOUNT_USERNAME" --password "$NORDACCOUNT_PASSWORD"
```

Connect to VPN (examples)
```
    # connect to any server in Canada
    docker exec $CID nordvpn connect Canada

    # connect to any server in Vancouver, Canada
    docker exec $CID nordvpn connect Canada Vancouver

    # connect to any server in Toronto
    docker exec $CID nordvpn connect Toronto
```

Disconnect from VPN
```
    docker exec $CID nordvpn disconnect
```

List available commands
```
    docker exec $CID nordvpn --help
```

## License

* [MIT License](LICENSE.md)

## References:

* [How to build the NordVPN Docker image?](https://support.nordvpn.com/Connectivity/Linux/1507838432/How-to-build-the-NordVPN-Docker-image.htm)
* [Installing NordVPN on Debian, Ubuntu, Raspberry Pi, Elementary OS & Linux Mint](https://support.nordvpn.com/Connectivity/Linux/1325531132/Installing-and-using-NordVPN-on-Debian-Ubuntu-Raspberry-Pi-Elementary-OS-and-Linux-Mint.htm)
* [Use the Docker command line](https://docs.docker.com/engine/reference/commandline/cli/)
