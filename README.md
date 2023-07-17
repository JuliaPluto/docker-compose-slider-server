# Deploying PlutoSliderServer with Docker (compose)

1. Make a cool pluto notebook! 🎉
2. Find a server you can run on the internet (that has an IPv4) (`your.domain.net`)
3. Find a domain name and make it point to `your.domain.net`
4. Install docker (Installation [instructions](https://docs.docker.com/desktop/install/linux-install/)) on your server
5. Build the docker container with the Dockerfile attached here
```bash
docker build -t pluto-slider-server .
```

6. In nginx.conf, change the your.domain.com domain to your domain
7. In compose.yaml, change the you@your.domain.net to your@email.com and the domains to your domains (needs `-d domain.com`). You can add more than one domain, but make sure to use the first domain as a folder name in nginx.conf
8. Comment out the SSL files from the nginx.conf file
9. Run `docker compose up` once, let certbot create certificates initially
10. Control+C, then uncomment the SSL files from the nginx.conf file to actually load the certificates.
11. Change the `compose.yaml` to point to the corrent git folder (instead of `your-folder-with-git-and-notebooks`) with Pluto notebooks that you want to deploy
12. Make sure `docker` will run on startup: usually `sudo systemctl enable docker`
13. Run `docker compose up -d` to start the services orchestra in the background
14. Push changes to your repo to see them updating!



