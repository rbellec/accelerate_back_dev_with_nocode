# TODO

- Rétablir la connexion à la console de commande rabbitmq par traefik
- Configuration statique des files d'attente dans rabbitmq
- Créer un engine rails dans l'app pour
  - Configurer les Gem (Bunny ?) & envoyer des messages amqp
  - Valider récéption sur trigger n8n
  - Ajouter gem pour récéption des messages amqp dans l'engine (sneakers ?)
  - Valider cycle envoi/récéption (un micro worker qui retourne "reçu" avec un élément du message envoyé ? Gardé pour valider l'installation.)

Voir :
1. https://medium.com/@clementrollon/rails-rabbitmq-actioncable-how-to-build-realtime-microservice-part-1-c25bf00c5187
2. https://medium.com/@clementrollon/rails-rabbitmq-actioncable-how-to-build-realtime-microservice-part-2-23c5f15c3fef

Passer aux exemples. En vrac :
- Publier des message slack à partir du n8n (ne peut pas en recevoir sans être sur un serveur public).
- Possibilité de plug in chat GPT ? -> accès au planning entre deux dates (sur le mois max ? API publique ?) en csv ou json par ex, chatGpt peut en extraire des informations.
- Si plug in Ok, publi sur slack ou envoir par mail/sms de l'information demandée.
- Démo d'accès direct à la BDD (ex super utilisateurs)

Démo :
- Bot avec Chagpt qui va chercher le ticket de caisse et suit un raisonnement pour essayer de trouver le problème ou, au moins, isoler les causes possibles, les plannables concernés, etc.
- Lister les super users dans slack. Voir si on peut croiser avec les users slack ?
- Annoncer tout nouvel abonnement dans slack (avec Chargebee ? On peut commencer avec le staging)
- Un export excel par chat GPT.


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
