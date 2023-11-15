# No-code and back development

Can we use No-codes tools to complement back development ?

Here are some tests around this idea.

## Reminders

Default password for rabbitmq management console is `guest`/`guest`

## Access

All services can be accessed through their name via traefik and a personal TLD.
Currently rabbitmq configuration has to be updated and can be accessed only via its port on
localhost (http://rabbitmq.local:15672/#/). Open port in docker-compose file to access it from outside.

### Traefik dashboard

Once your /etc/hosts configured, you can access dashboard at http://traefik.local/dashboard/

If you want to access the dashboard & API in insecure mode, you need to uncomment the 2 lines in docker-compose.yml
(or better, configure them in docker-compose.override.yml). A commented section is placed in docker-compose.override.example.yml.

# - "--api.insecure=true" # To open console and API on port 8080
# - "8080:8080" # Only for "insecure mode"

traefik  dashboard : http://localhost:8080/dashboard/

## Certificates

Certificate have been generated using (minica)[https://github.com/jsha/minica], you can find a walkthrough to create and install local certificates here : https://blog.ruanbekker.com/blog/2020/12/23/https-for-local-development-with-minica/.

Method : https://traefik.io/blog/traefik-2-tls-101-23b4fbee81f1/

TODO: Write steps to add a certificate for a service (generate in the minica directory: `minica --domains '*.local.com'`, copy in configuration/... add to configuration directory)

Note : Besoin de sql studio pour changer le MDP dans la BDD SQL Lite après installation
