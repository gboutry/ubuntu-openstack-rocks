# barbican-api ROCK

This is a ROCK OCI image for barbican-api.

More information is coming.

For now, if you want to play with it:

```bash
> sudo snap install rockcraft --edge --classic
> rockcraft pack
```

Now that you have created the ROCK, you can import it into
your local docker repository. Using skopeo is a good idea as
it will help ensure that all layers of the image are imported
into docker (this is just the top layer).

```bash
> skopeo --insecure-policy copy oci-archive:barbican-api_2023.2_amd64.rock docker-daemon:barbican-api:2023.2
```

If you are interested in giving it a go in Microk8s, you can
export the image from your docker registry and then into the
microk8s registry:

```bash
> docker save barbican-api:2023.2 > ./barbican-api_2023.2.tar
> microk8s ctr image import ./barbican-api_2023.2.tar
# Try with sunbeam
> juju attach-resource barbican-api barbican-api-image=barbican-api:2023.2
```
