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
  


