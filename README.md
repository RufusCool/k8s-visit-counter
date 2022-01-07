![Alt text](https://raw.githubusercontent.com/RufusCool/k8s-visit-counter/main/layout/k8s.png)
# k8s-visit-counter

  Exemplos ao subir PODs no K8S
  Como fazer um simples deployments e operações básicas no Kubernetes.

  Aplicação criada em Ruby, utilizado a gem redis para nos comunicar com o Redis e a gem sinatra pra expor uma interface web

# Categorías e Comandos

  Mostrar Pods Rodando
- kubectl get pods
- watch kubectl get pods -o wide

  Scale
- kubectl scale deploy -n nomenamespace visit-counter --replicas=6

  Rollout
- kubectl rollout restart deploy -n nomenamespace visit-counter

  Visualizar logs do Pod
- kubectl  logs nomedopod

  Aplicar Deploy k8s, exemplo abaixo do meu caso, mude para o nome que criou para executar a ação.
- kubectl apply -f visit-counter-deployment.yaml
- deployment.apps/visit-counter created

- kubectl apply -f visit-counter-service.yaml
- service/visit-counter-service created

  Validar Pods e Services
- kubectl get pods,svc

  Pra ver os logs de todos os Pods, podemos fazer um filtro pela label que definimos no yaml
- kubectl logs --follow --tail 0 --selector="app=dummy-logger-deployment"

  Redirecionar uma porta específica para nossa máquina através do comando kubectl port-forward
- kubectl port-forward svc/visit-counter-service 2000:3000
