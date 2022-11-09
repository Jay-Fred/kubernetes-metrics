**一、修改resource-reader配置文件**

	# wget  https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

**二、修改deployment配置文件**

    # vim components.yaml
	  resources:
	  - pods
	  - nodes
	  - nodes/stats
	  - namespaces

	# vim metrics-server-deployment.yaml
	      - name: metrics-server
	        image: registry.cn-hangzhou.aliyuncs.com/google_containers/metrics-server:v0.6.1
	        command:
	        - /metrics-server
	        - --metric-resolution=30s
	        - --kubelet-insecure-tls
	        - --kubelet-preferred-address-types=InternalIP,Hostname,InternalDNS,ExternalDNS,ExternalIP
	# kubectl apply -f .
	# kubectl top nodes
	# kubectl top pods -A
