
# docker-electrumx

> Run an Electrumx server with one command

An easily configurable Docker image for running an Electrumx server.

## Usage

```
docker run \
  -v /home/username/electrumx:/data \
  -e DAEMON_URL=http://user:pass@host:port \
  -e COIN=Groestlcoin \
  -p 50002:50002 \
  groestlcoin/electrumx
```

If there's an SSL certificate/key (`electrumx.crt`/`electrumx.key`) in the `/data` volume it'll be used. If not, one will be generated for you.

You can view all ElectrumX environment variables here: https://github.com/kyuupichan/electrumx/blob/master/docs/environment.rst

### TCP Port

By default only the SSL port is exposed. You can expose the unencrypted TCP port with `-p 50001:50001`, although this is strongly discouraged.

### WebSocket Port

You can expose the WebSocket port with `-p 50004:50004`.

### RPC Port

To access RPC from your host machine, you'll also need to expose port 8000. You probably only want this available to localhost: `-p 127.0.0.1:8000:8000`.

If you're only accessing RPC from within the container, there's no need to expose the RPC port.

### Version

You can also run a specific version of ElectrumX if you want.

```
docker run \
  -v /home/username/electrumx:/data \
  -e DAEMON_URL=http://user:pass@host:port \
  -e COIN=Groestlcoin \
  -p 50002:50002 \
  groestlcoin/electrumx:version-1.9.1
```

## License

MIT © Luke Childs
