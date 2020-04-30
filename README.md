Deployment requirements:

1. You own a domain that you have pointed to cloudflare

2. You have a wildcard 'A' record pointing to your public IP.

```
A              *          222.222.222.222             Auto
```

3. You have a cloudflare API zone token with the correct permissions and scope

```
Edit zone DNS	Zone.Zone Settings, Zone.Zone, Zone.DNS	All zones
```

3. port 80 and 443 are forwarded to your docker host from a public ip

4. You have deployed swarm mode on your docker host(s)

```docker swarm init```

5. You have created a docker overlay network named 'traefik-public'

6. Supply the required env vars to the stack and deploy:

```
docker stack deploy -c docker-compose.yml nodered
```

When you successfully get a lets-encrypt staging cert, you can comment out the staging line in its entirety, delete the stack, and deploy the stack again. 

You will need to hard-refresh your browser for it to pick up your new cert (some browsers are bad for this - use incognito mode to verify your cert)

Some routers will need a dns record added for accessing your site from inside your network. 

Coming Next:

- Oauth w/ google login
