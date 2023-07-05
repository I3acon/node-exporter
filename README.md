# Instructions on how to set up monitoring stack for your cosmos validator

## Prerequisites

### Install exporters on validator node
First of all you will have to install exporters on validator node. For that you can use one-liner below
```
wget -O install_exporter.sh https://raw.githubusercontent.com/I3acon/node-exporter/main/install_exporter.sh && chmod +x install_exporter.sh && ./install_exporter.sh```

make sure following ports are open:
- `9100` (node-exporter)

## Deployment
Monitoring stack needs to be deployed on seperate machine to be able to notify in case if validator goes down! 
To run monitoring stack you dont need beastly server with multiple cores. It will be more than enough to run it on smallest available vps

### System requirements
Ubuntu 20.04 / 1 VCPU / 2 GB RAM / 20 GB SSD

### Install monitoring stack
To install monitirng stack you can use one-liner below
```
wget -O install_monitoring.sh https://raw.githubusercontent.com/I3acon/node-exporter/main/install_monitoring.sh && chmod +x install_monitoring.sh && ./install_monitoring.sh
```

### Run docker-compose
Deploy the monitoring stack
```
cd $HOME/cosmos_node_monitoring && docker-compose up -d
```

ports used:
- `9090` (prometheus)
- `9999` (grafana)



## Dashboard contents


- **Hardware health** - system hardware metrics. cpu, ram, network usage

![image](https://user-images.githubusercontent.com/50621007/160630213-5e92b3ce-92c9-4f48-8856-383ca884b621.png)

## Cleanup all container data
```
cd $HOME/cosmos_node_monitoring
docker-compose down
docker volume prune -f
```

## Reference list
Resources I used in this project:
- Grafana Hardware health [AgoricTools by Chainode](https://github.com/Chainode/AgoricTools)
