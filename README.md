# No-code and back development

Can we use No-codes tools to complement back development ?

Here are some tests around this idea.

## Reminders

Default password for rabbitmq management console is `guest`/`guest`


## Certificates

Certificate have been generated using (minica)[https://github.com/jsha/minica], you can find a walkthrough to create and install local certificates here : https://blog.ruanbekker.com/blog/2020/12/23/https-for-local-development-with-minica/.

Method : https://traefik.io/blog/traefik-2-tls-101-23b4fbee81f1/

TODO: Write steps to add a certificate for a service (generate in the minica directory: `minica --domains '*.local.com'`, copy in configuration/... add to configuration directory)