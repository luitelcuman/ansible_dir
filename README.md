# Ansible Playbook: Monitoring Setup with Prometheus and Grafana

## Introduction

This Ansible playbooks automates the setup of monitoring for various services using Prometheus and Grafana. The playbook includes roles for `node_exporter`, `mysqld_exporter`, `rabbitmq_exporter`, and `redis_exporter`. It also other two roles `add-scrape-config` configures scrape targets in Prometheus and `import-grafana-dashboard` creates Grafana dashboards for each exporter.

## Requirements

- Ansible: Ensure that you have Ansible installed on your control machine.

- Prometheus: Set up Prometheus on a target server. Ensure that the Prometheus server is accessible and configured in your hosts.

- Grafana: Install Grafana on a target server. Make sure that Grafana is accessible and configured in your hosts.

## Usage

1. Clone this repository to your Ansible control machine:

`git clone https://github.com/luitelcuman/ansible_dir.git`


2. Update the hosts (`hosts`) with your target hosts. Ensure that each group of hosts is correctly configured.

3. Modify the playbook variables and configurations as needed. Customize the exporter configurations in the variable files located in the `roles/vars` directory.

4. Run the playbook using the following command with specific tags:

`ansible-playbook mysqld_exporter.yml --tags mysqld` // To install mysqld_exporter   
`ansible-playbook node_exporter.yml --tags node` // To install node_exporter  
`ansible-playbook redis_exporter.yml --tags redis` // To install redis_exporter  
`ansible-playbook rabbitmq_exporter.yml --tags rabbitmq` // To install rabbitmq_exporter  

5. Use following tags:
    `prometheus`: to config `prometheus.yml` for specific exporter  
    `grafana` : to create grafana dashboard for sepecific exporter  

6. The playbooks will apply the roles to the specified hosts, install and configure the Prometheus exporters, add scrape targets to the Prometheus configuration, and create Grafana dashboards.

## Roles

- **node_exporter**: Installs and configures Prometheus Node Exporter for system-level metrics.

- **mysqld_exporter**: Installs and configures Prometheus MySQL Exporter for MySQL database metrics.

- **rabbitmq_exporter**: Installs and configures Prometheus RabbitMQ Exporter for RabbitMQ metrics.

- **redis_exporter**: Installs and configures Prometheus Redis Exporter for Redis metrics.

## Customization

You can customize the exporter configurations by editing the appropriate variables in the variable files. For example, customize every configuration in `roles/vars/vars.yml`.

## Grafana Dashboards

Grafana dashboards for exporter are automatically created after the specific playbook runs . You can access the Grafana web interface to view and manage these dashboards.

- Grafana URL: [Your Grafana URL]

## Contributing

Contributions to this playbook are welcome. If you have improvements or additional exporters to add, please fork this repository, make your changes, and submit a pull request.

## License

This playbook is open-source and available under the [MIT License](LICENSE).

## Contact

If you have questions or need assistance, feel free to contact us at luitelcuman@gmail.com.

