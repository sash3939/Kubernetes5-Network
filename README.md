# Домашнее задание к занятию «Сетевое взаимодействие в K8S. Часть 2»

### Цель задания

В тестовой среде Kubernetes необходимо обеспечить доступ к двум приложениям снаружи кластера по разным путям.

------

### Чеклист готовности к домашнему заданию

1. Установленное k8s-решение (например, MicroK8S).
2. Установленный локальный kubectl.
3. Редактор YAML-файлов с подключённым Git-репозиторием.

------

### Инструменты и дополнительные материалы, которые пригодятся для выполнения задания

1. [Инструкция](https://microk8s.io/docs/getting-started) по установке MicroK8S.
2. [Описание](https://kubernetes.io/docs/concepts/services-networking/service/) Service.
3. [Описание](https://kubernetes.io/docs/concepts/services-networking/ingress/) Ingress.
4. [Описание](https://github.com/wbitt/Network-MultiTool) Multitool.

------

### Задание 1. Создать Deployment приложений backend и frontend

1. Создать Deployment приложения _frontend_ из образа nginx с количеством реплик 3 шт.

<img width="362" alt="frontend" src="https://github.com/user-attachments/assets/2ec301a6-0bc4-4a13-8058-4d9b5180694e">

2. Создать Deployment приложения _backend_ из образа multitool. 

<img width="401" alt="backend" src="https://github.com/user-attachments/assets/fbca5fa6-35f3-429e-a081-b549de113942">

3. Добавить Service, которые обеспечат доступ к обоим приложениям внутри кластера. 

<img width="518" alt="backend+frontend svc" src="https://github.com/user-attachments/assets/e5cc38aa-a547-4423-bde6-196d7f3b4aed">

4. Продемонстрировать, что приложения видят друг друга с помощью Service.
Сначала с pods frontend, затем обратно с backend на frontend nginx:

<img width="740" alt="curl with service frontend+backend" src="https://github.com/user-attachments/assets/56666986-bf96-4896-a4e6-005cb8327613">

5. Предоставить манифесты Deployment и Service в решении, а также скриншоты или вывод команды п.4.

[frontend.yaml](https://github.com/sash3939/Kubernetes5-Network/blob/main/frontend.yaml)

[backend.yaml](https://github.com/sash3939/Kubernetes5-Network/blob/main/backend.yaml)

[frontend-svc.yaml](https://github.com/sash3939/Kubernetes5-Network/blob/main/frontend-svc.yaml)

[backend-svc.yaml](https://github.com/sash3939/Kubernetes5-Network/blob/main/backend-svc.yaml)

------

### Задание 2. Создать Ingress и обеспечить доступ к приложениям снаружи кластера

1. Включить Ingress-controller в MicroK8S.

<img width="443" alt="Ingress enable" src="https://github.com/user-attachments/assets/a22c5d9f-8266-4d7a-81b5-df46d81c357f">

<img width="509" alt="status" src="https://github.com/user-attachments/assets/a6571c39-ce7d-4dcc-a1ee-3fd0f4dda054">

2. Создать Ingress, обеспечивающий доступ снаружи по IP-адресу кластера MicroK8S так, чтобы при запросе только по адресу открывался _frontend_ а при добавлении /api - _backend_.

<img width="385" alt="create ingress" src="https://github.com/user-attachments/assets/e1dfaf92-1fc1-4928-a9c4-75fe86c62fe6">

3. Продемонстрировать доступ с помощью браузера или `curl` с локального компьютера.

<img width="736" alt="curl" src="https://github.com/user-attachments/assets/6c1d3637-dc4f-4474-85ea-32b9a23ea220">

<img width="601" alt="test browser" src="https://github.com/user-attachments/assets/6b600aa1-3353-40c4-a18a-fedc1f095967">

<img width="646" alt="test-api browser" src="https://github.com/user-attachments/assets/025e5cdc-dff2-4326-afc0-e6365d9b679e">

4. Предоставить манифесты и скриншоты или вывод команды п.2.

[ingress.yaml](https://github.com/sash3939/Kubernetes5-Network/blob/main/ingress.yaml)

------

### Правила приема работы

1. Домашняя работа оформляется в своем Git-репозитории в файле README.md. Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.
2. Файл README.md должен содержать скриншоты вывода необходимых команд `kubectl` и скриншоты результатов.
3. Репозиторий должен содержать тексты манифестов или ссылки на них в файле README.md.

------
