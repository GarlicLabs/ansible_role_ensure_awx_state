# ansible_role_ensure_awx_state

[![Validate infrastructure as code](https://github.com/garliclabs/ansible_role_ensure_awx_state/actions/workflows/validation.yml/badge.svg)](https://github.com/garliclabs/ansible_role_ensure_awx_state/actions/workflows/validation.yml)

Manages the installation state of awx in a kubernetes cluster via helm

## Requirements

Kubernetes, Helm, kubectl

## Role Variables

**awx_namespace:** Kubernetes namespace in that awx will be deployed  
**awx_name:** Name of this awx installation  
**awx_state:** State of the deployment, can be either present or absent
**awx_chart_version:** Version of gitea helm chart
**awx_kubeconfig:** Path to the kubeconfig for your kubernetes cluster
**awx_secret:** Key for awx to encrypt data  

**awx_value_path:** Provide a path to your own helm value file  

**Or** use our default value file and fill out following defaults  

**awx_postgres_database:** Awx database name in your provided postgres database  
**awx_postgres_host:** Host of your postgres database  
**awx_postgres_port:** Port of your postgres database  
**awx_postgres_username:** Username that awx will use to authenticate against the provided postgres database  
**awx_postgres_password:** Password that awx will use to authenticate against the provided postgres database  
**awx_hostname:** Hostname under awx will be reachable  
**awx_admin_username:** Admin username for awx  
**awx_admin_password:** Admin password for awx
**awx_admin_email:** Admin email address for awx admin user  
**awx_storage_class:** Kubernetes storage class  
**awx_storage_size:** Size of the persistent volume  

## Development

### Testing

* Create venv: `python3 -m venv ./venv`
* Install pip requirements: `venv/bin/pip install -r pip_requirements.txt`
* Execute tests `venv/bin/molecule test`

### Linting & static security analyser

Both the linter and the static security analyser are running on each push on the github actions pipeline.  

* As linter [ansible-lint](https://ansible.readthedocs.io/projects/lint/) is used. For installation documentation see [ansible lint installing](https://ansible.readthedocs.io/projects/lint/)
  * Just run `ansible-lint`

* To check if there are any passwords, tokens... hardcoded, [kics](https://kics.io/index.html) is used to ensure a secure IaC repository.  
  * Run it locally `docker run -t -v $PWD:/path checkmarx/kics:latest scan -p /path -o "/path/"`

## License

GNU General Public License version 3
