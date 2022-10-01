# gdstack

1. Deploy stack

git clone https://github.com/gtc13/gdstack.git

docker stack deploy -c gdstach/grafa_loft.yml monitu

2. Add prometheus datasource with address http://prometheus:9090 to grafana
3. Add these three lines to the bottom of /var/lib/docker/volumes/monitoring_prom-configs/_data/_prometheus.yml file, to scrape_configs: section:

-job_name: 'node-exporter'

static_configs:
  - targets: ['node-exporter:9100']

4. Reload prometheus config via this command:

$ docker ps | grep prometheus | awk '{print $1}' | xargs docker kill -s SIGHUP
 
5. Import this dashboard: https://grafana.com/grafana/dashboards/1860 to grafana

Att! Docker swarm init must be ON
