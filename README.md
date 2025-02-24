# TLS Certificate Renewal Automation : Prom, Ansible and github actions.

A quick repo to automate SSL renewal for a Nginx Proxies. 
The reasonable thing would be cron and a bash script but we dont do that here

## Components

### Promethes stack
I already have prometheus, a blackbox exporter and grafana monitoring and checking my 3 Nginx Servers.
Promethes gathers TLS certificate expiration date from the sites via the blackbox exporter
Grafana, with promethes as a data source, triggers alert and sends webhook based on remaining time on the certificates

### Github
Github hosts the repo, and the runners( will start self hosting runners soon).
Github receives the webhook and triggers github action
Github action spins up ansible container that updates the certificates

### Ansible
Ansible playbook templates the DNS api token and bash script to run the LetsEncrypt Certbot container which updates the current TLS certificates with newly updated and signed certs. 

## TODO

### Security
Research security to confirm its safe to put vaults in a public repo. 
