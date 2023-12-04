# Desafío núemro 9 - CI/CD y Kubernetes

En el presente desafío, vuelvo a utilizar el stack de Ubuntu Server nativo que utilicé para el desafío número 8.
En este stack tengo instalado minikube y configurado kubectl como herramienta de linea de comandos.


## Instalación de ArgoCD

Comencé creando un namespace específico para realizar este desafío con el siguiente comando:
`kubectl create namespace tp9`
Luego, utilizando kubectl instalé ArgoCD desde el repo oficial
`kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`
Finalmente, utilizando la ip de mi nodo(llamado "minikube", el cual creé para el practico anterior), enruté el trafico entre esta ip con el puerto de ArgoCD server hacia el puerto 3001 de mi entorno (Ubuntu Server nativo), con el siguiente comando.
`sudo iptables -t nat -A PREROUTING -p tcp --dport 8080 -j DNAT --to-destination 192.168.49.2:31482`
Con esto, ya pude acceder al panel web de ArgoCD.

