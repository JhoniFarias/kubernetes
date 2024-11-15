# Comandos Básicos

- `kubectl get pods`: Lista todos os pods no namespace atual.
- `kubectl get pods --watch`: Acompanha o status em tempo real.
- `kubectl get services`: Lista todos os serviços.
- `kubectl get nodes`: Lista todos os nós no cluster.
- `kubectl describe <recurso>`: Exibe detalhes de um recurso específico.
  - `kubectl describe pod <nome-do-pod>`: Mostra informações detalhadas de um pod específico.
- `kubectl logs`: Mostra os logs de um pod ou contêiner específico.
  - `kubectl logs <nome-do-pod>`: Exibe os logs do pod.
  - `kubectl logs <nome-do-pod> -c <nome-do-contêiner>`: Exibe os logs de um contêiner específico dentro de um pod.
- `kubectl exec`: Executa comandos dentro de um contêiner em um pod.
  - `kubectl exec -it <nome-do-pod> -- /bin/bash`: Abre um shell interativo dentro de um contêiner.
- `kubectl delete pod <nome-do-pod>`: Exclui um pod específico.
- `kubectl delete -f <arquivo.yaml>`: Exclui recursos com base em um arquivo YAML.
- `kubectl scale`: Escala o número de réplicas de um recurso.
  - `kubectl scale deployment <nome-do-deployment> --replicas=<número>`: Altera o número de réplicas para um deployment.
- `kubectl edit deployment <nome-do-deployment>`: Abre o editor de texto padrão para editar a configuração de um deployment.
- `kubectl port-forward`: Encaminha uma porta local para um pod, permitindo o acesso a serviços dentro do cluster a partir de sua máquina local.
  - `kubectl port-forward pod/<nome-do-pod> <porta-local>:<porta-no-pod>`: Encaminha a porta local para a porta do pod.
- `kubectl get events`: Lista eventos recentes que ocorreram no cluster, útil para debugging.

# Tipos de Serviços

- `Cluster-IP`: Comunicação interna.
- `NodePort`: Comunicação externa.
- `LoadBalancer`: Comunicação externa, geralmente utilizado em cloud.

# Configurações

- **ConfigMap**: Mapeia variáveis de ambiente ou configurações da aplicação.
- **Secrets**: Podem ser criados diretamente no console ou através de um arquivo do tipo Opaque com os valores das chaves codificados em base64.

# Volumes

- **PV (Persistent Volume)**:
  - `emptyDir`: Cria um volume assim que o pod inicia e deleta o volume assim que o pod é encerrado. Usado para compartilhar arquivos temporários.
  - `hostPath`: Mapeia um volume na máquina host.
- **PVC (Persistent Volume Claim)**: Utilizado para fazer a ligação de um volume e configura o tipo de armazenamento.

# Health Check

- **Probes**: Recursos para acompanhar o healthcheck da aplicação.
  - **Liveness Probe**: Verifica se o pod está em execução.
  - **Readiness Probe**: Verifica se o pod está pronto para receber requisições (ideal quando o pod demora para carregar configurações).

# AutoScale

- Instalar o metric-server:
  ```bash
  kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.7.2/components.yaml

Teste de Desempenho

para testar o hpa podemos utilizar o k6
segue o exemplo de como instalar
choco install k6
para rodar:
k6 run requests-k6.js

Rodar todos os yamls e percorrer todas as pastas
kubectl apply -f . -R
