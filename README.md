 - docker exec -i -t 1b3330603243 sh
 - docker stop 1b3330603243
 - docker ps
 - kubectl get pods
 - kubectl get namespace
 - docker images 
 - kubectl delete rc kubia
 - kubectl get rc
 - kubectl get replicationcontroller
 - kubectl get service
 - docker login
- docker create -t kubia .
 - docker tag kubia prashanthsriram145/kubia
 - docker push prashanthsriram145/kubia
 - kubectl run kubia --image=prashanthsriram145/kubia --port=8080 --generator=run/v1
 - kubectl delete rc kubia
 - kubectl run kubia --image=prashanthsriram145/kubia --port=8080 --generator=run/v1
 - kubectl expose rc kubia --type=LoadBalancer --name kubia-http
 - kubectl get service
 - kubectl get service
- minikube service kubia-http - TO GET ENDPONT FOR ACCESSING APPLICATION
- kubectl scale rc kubia --replicas=2
- kubectl describe pod kubia-bsnb4
- kubectl cluster-info | grep dashboard
- minikube dashboard

SECOND:
- kubectl get pod kubia-bsnb4 -o yaml
kubectl apply -f kubia-manual.yaml 
- kubectl apply -f kubia-manual.yaml 
- kubectl delete service kubia-http
- kubectl logs kubia-manual
- kubectl port-forward kubia-manual 8888:8080
- kubectl apply -f kubia-manual-with-labels.yaml 
- kubectl get pods --show-labels
- kubectl get pods -L cration_method,env
- kubectl get pod kubia-manual-v2 env=debug --overwrite
- kubectl label pod kubia-manual-v2 env=debug --overwrite
- kubectl get pods -l env=debug
- kubectl get pods -l '!env1'
- kubectl apply -f kubia-gpu.yml 
- kubectl get ns
- kubectl apply -f custom-namespace.yml 
- kubectl get namespace
- kubectl config set-context --current --namespace custom-namespace
- kubectl delete pod kubia-gpu
- kubectl delete pods -l env=prod
- kubectl delete pods --all
- kubectl delete namespace custom-namespace
- kubectl delete all --all
- kubectl logs kubia-liveness --previous

- minikube start
- kubectl port-forward kubia-pod-emptydir 8080:80
- kubectl exec -i -t gitrepo-volume-pod sh
- kubectl describe pv mongodb-pv
- kubectl get pv
- kubectl get pvc
- kubectl logs mongodb-pvc
- kubectl get sc

- kubectl create configmap sameple-cm --from-literal=foo=bar
- kubectl get configmap sameple-cm -o yaml
- kubectl create configmap my-config --from-file=config-file.conf
- kubectl create configmap my-config --from-file=/path/to/dir


- kubectl get secrets
- kubectl get secret fortune-https -o yaml
- kubectl edit configmap fortune-config
- kubectl logs fortune-https -c web-server
- kubectl port-forward fortune-https 8443:443
- kubectl port-forward fortune-https 8443:443 &
- curl https://localhost:8443 -k -v
- kubectl exec fortune-https -c web-server -- mount | grep certs
- kubectl create secret docker-registry mydockerhubsecret --docker-username=myusername --docker-password=mypassword --docker-email=my.email@provider.com


  - kubectl exec downward env
  - kubectl exec downward-volume ls  /etc/downward
  - kubectl exec downward-volume cat /etc/downward/labels
  - kubectl cluster-info
  - kubectl proxy &
  - curl localhost:8001
  - curl http://localhost:8001/apis/batch/v1/jobs
  - curl http://localhost:8001/apis/batch/v1/namespaces/default/jobs/my-job
  - kubectl logs curl-with-ambassador -c main
  - kubectl logs curl-with-ambassador -c ambassador
 - curl --cacert /var/run/secrets/kubernetes.io/serviceaccount/ca.crt https://10.96.0.1:443
- export CURL_CA_BUNDLE=/var/run/secrets/kubernetes.io/serviceaccount/ca.crt
- curl https://kubernetes
- TOKEN=$(cat /var/run/secrets/kubernetes.io/serviceaccount/token)
- curl -H "Authorization: Bearer $TOKEN" https://kubernetes
- kubectl create clusterrolebinding permissive-binding --clusterrole=cluster-admin --group=system:serviceaccounts
- NS=$(cat /var/run/secrets/kubernetes.io/serviceaccount/namespace)
 - curl -H "Authorization: Bearer $TOKEN" https://kubernetes/api/v1/namespaces/$NS/pods
  
579  kubectl apply -f kubia-rc-service-v1.yml 
  583  minikube service kubia
  584  while true; do curl http://192.168.99.105:30005; done
  585  kubectl delete rc --all
  586  kubectl apply -f kubia-deployment-v1.yml 
  587  kubectl get deployments
  588  kubectl rollout status deployment kubia
  590  kubectl get replicasets
  591  kubectl patch deployment kubia -p '{"spec": {"minReadySeconds": 10}}'
kubectl set image deployment kubia nodejs=luksa/kubia:v4
kubectl rollout pause deployment kubia
kubectl rollout resume deployment kubia
kubectl rollout status deployment kubia


HELM:
- helm repo add bitnami https://charts.bitnami.com/bitnami 
- helm install redis bitnami/redis --namespace=default 
- minikube config set memory 4000
- minikube start
- minikube stop
- minikube delete
- helm repo list
- helm repo update
- helm repo remove bitnami
- helm plugin install $URL
- helm plugin list
- helm plugin unistall $PLUGIN
- helm plugin update $PLUGIN
- helm search hub
- helm search repo
- helm search hub wordpress
- helm search hub wordpress --max-col-width=0
- helm search hub wordpress --output yaml
- helm repo add bitnami https://charts.bitnami.com/bitnami
- helm search repo wordpress
- helm search repo wordpress --versions
- helm show chart bitnami/wordpress
- helm search values wordpress --versions
- helm search readme wordpress --versions
- kubectl create namespace chapter3
-

 506  helm install wordpress bitnami/wordpress --values=wordpress-values.yml --namespace chapter3 --version 8.1.0
  507  helm list --namespace chapter3
  512  helm get hooks wordpress --namespace chapter3
  514  helm get manifest wordpress --namespace chapter3
  519  helm get notes wordpress --namespace chapter3
  520  helm get values wordpress --workspace chapter3
  521  helm get values wordpress --namespace chapter3
  522  helm get values wordpress --all --namespace chapter3
  525  helm get all wordpress --namespace chapter3
  531  kubectl get all -l app=wordpress --namespace chapter3
  535  export HELM_NAMESPACE=chapter3
  536  helm env
  export NODE_PORT=$(kubectl get --namespace chapter3 -o jsonpath="{.spec.ports[0].nodePort}" services wordpress)
  539    export NODE_IP=$(kubectl get nodes --namespace chapter3 -o jsonpath="{.items[0].status.addresses[0].address}")
  540    echo "WordPress URL: http://$NODE_IP:$NODE_PORT/"
  541    echo "WordPress Admin URL: http://$NODE_IP:$NODE_PORT/admin"
  542   echo Username: helm-user
  543    echo Password: $(kubectl get secret --namespace chapter3 wordpress -o jsonpath="{.data.wordpress-password}" | base64 --decode)
  563  helm update wordpress bitnami/wordpress 
  564  helm update wordpress bitnami/wordpress --namespace chapter3
 helm upgrade wordpress bitnami/wordpress --values=wordpress-values.yml --namespace chapter3 --version 8.1.0
 helm upgrade wordpress bitnami/wordpress --values=wordpress-values.yml --namespace chapter3 --version 8.1.0
 kubectl get secrets -n chapter3
 helm history wordpress -n chapter3
 helm get values wordpress --revision 2 -n chapter3
 helm rollback wordpress 1 -n chapter3
 helm uninstall wordpress





NAME: redis
LAST DEPLOYED: Sat Nov 21 12:14:21 2020
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
** Please be patient while the chart is being deployed **
Redis can be accessed via port 6379 on the following DNS names from within your cluster:

redis-master.default.svc.cluster.local for read/write operations
redis-slave.default.svc.cluster.local for read-only operations


To get your password run:

    export REDIS_PASSWORD=$(kubectl get secret --namespace default redis -o jsonpath="{.data.redis-password}" | base64 --decode)

To connect to your Redis server:

1. Run a Redis pod that you can use as a client:
   kubectl run --namespace default redis-client --rm --tty -i --restart='Never' \
    --env REDIS_PASSWORD=$REDIS_PASSWORD \
   --image docker.io/bitnami/redis:6.0.9-debian-10-r13 -- bash

2. Connect using the Redis CLI:
   redis-cli -h redis-master -a $REDIS_PASSWORD
   redis-cli -h redis-slave -a $REDIS_PASSWORD

To connect to your database from outside the cluster execute the following commands:

    kubectl port-forward --namespace default svc/redis-master 6379:6379 &
    redis-cli -h 127.0.0.1 -p 6379 -a $REDIS_PASSWORD
