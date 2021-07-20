

For this prometheouse monitoring installation it is required a K8s cluster and kubectl,docker,helm and Git installed server. 

Componantes to deploy: 

1. Prometheus
2. Alertmanager
3. Grafana
4. Process counter exporter 

Architecure Diagram : 

Installation: 

01.First need to create custom process count exporter docker image 
Navigate to CPCExporter directory

    $ docker build . -t <docker-repo-url>/custom-exporter:v1
    $ docker push <docker-repo-url>/custom-exporter:v1


02.Monitoring setup installation
   
   --Replace the custom-exporter docker image

       $ vi /HelmCharts/process-counter-exporter/values.yaml


  --Update alertmanager email and slack config

       $ vi /HelmCharts/alertmanager/values.yaml


03. Go to the Helm

   03.1 Install prometheus. 
   
	 helm install prometheus prometheus
    
   03.2 Install grafana.
   
	 helm install grafana grafana 
    
   03.3 Install alertmanager 
   
	 helm install alertmanager alertmanager
    
   03.4 Install process-counter-exporter 
   
	 helm install process-counter-exporter process-counter-exporter 

