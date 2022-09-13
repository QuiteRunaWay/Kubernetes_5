# Домашнее задание к занятию "12.5 Сетевые решения CNI"
После работы с Flannel появилась необходимость обеспечить безопасность для приложения. Для этого лучше всего подойдет Calico.
## Задание 1: установить в кластер CNI плагин Calico
Для проверки других сетевых решений стоит поставить отличный от Flannel плагин — например, Calico. Требования: 
* установка производится через ansible/kubespray;
* после применения следует настроить политику доступа к hello-world извне. Инструкции [kubernetes.io](https://kubernetes.io/docs/concepts/services-networking/network-policies/), [Calico](https://docs.projectcalico.org/about/about-network-policy)

## Ответ: 

 
Создаем скриптом ВМ:

![image](https://user-images.githubusercontent.com/92969676/189821817-8726333e-0838-4c86-b9a3-1f6a602c94a7.png)

Далее при помощи kubspray разворачиваю кластер k8s 

![image](https://user-images.githubusercontent.com/92969676/189826950-783fe643-6bec-45da-b1f0-3a74302a3107.png)

![image](https://user-images.githubusercontent.com/92969676/189831427-3e4fa855-4292-4ca9-860a-195f5d828d25.png)

Конфигурация хостов кластера:

![image](https://user-images.githubusercontent.com/92969676/189827559-9cd89079-65fe-434c-a5ad-6444b2fb1ed7.png)

![image](https://user-images.githubusercontent.com/92969676/189827488-e874305a-9cc3-47d5-a251-72da9d3a422b.png)

Кластер разворачивается так, что у него плагин по умолчанию сразу стоит Calico, и кластер доступен по внешнему адресу 158.160.0.197 (при условии настройки нашей локальной машины. Сделал просто на будущее, если вдруг пригодится).

![Uploading image.png…]()




## Задание 2: изучить, что запущено по умолчанию
Самый простой способ — проверить командой calicoctl get <type>. Для проверки стоит получить список нод, ipPool и profile.
Требования: 
* установить утилиту calicoctl;
* получить 3 вышеописанных типа в консоли.

### Как оформить ДЗ?

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории
  
 
