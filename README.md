# Домашнее задание к занятию "12.5 Сетевые решения CNI"
После работы с Flannel появилась необходимость обеспечить безопасность для приложения. Для этого лучше всего подойдет Calico.
## Задание 1: установить в кластер CNI плагин Calico
Для проверки других сетевых решений стоит поставить отличный от Flannel плагин — например, Calico. Требования: 
* установка производится через ansible/kubespray;
* после применения следует настроить политику доступа к hello-world извне. Инструкции [kubernetes.io](https://kubernetes.io/docs/concepts/services-networking/network-policies/), [Calico](https://docs.projectcalico.org/about/about-network-policy)

## Ответ: 

Решил попрактиковаться в применении скриптом, по этому в данной ДЗ кластер разворачивал не локально, а я Yandex облаке. Скрипты и документацию использовал те же, что и в прошлых ДЗ, с ресурса преподавателя Андрея Копылова (https://github.com/aak74/kubernetes-for-beginners).
 
Создаем скриптом ВМ:

![image](https://user-images.githubusercontent.com/92969676/189821817-8726333e-0838-4c86-b9a3-1f6a602c94a7.png)

Далее при помощи kubspray разворачиваю кластер k8s: 

![image](https://user-images.githubusercontent.com/92969676/189826950-783fe643-6bec-45da-b1f0-3a74302a3107.png)

![image](https://user-images.githubusercontent.com/92969676/189831427-3e4fa855-4292-4ca9-860a-195f5d828d25.png)

Конфигурация хостов кластера:

![image](https://user-images.githubusercontent.com/92969676/189827559-9cd89079-65fe-434c-a5ad-6444b2fb1ed7.png)

![image](https://user-images.githubusercontent.com/92969676/189827488-e874305a-9cc3-47d5-a251-72da9d3a422b.png)

Кластер разворачивается так, что у него плагин по умолчанию сразу стоит Calico, и кластер доступен по внешнему адресу 158.160.0.197 (при условии настройки нашей локальной машины. Сделал просто на будущее, если вдруг пригодится).

![image](https://user-images.githubusercontent.com/92969676/189844034-3af3dfb3-5a45-4a53-8d79-79a185877d06.png)



Далее по предоставленной ссылке ознакомился со статьёй по настройки политики доступа из вне (https://docs.projectcalico.org/security/tutorials/kubernetes-policy-basic):

![image](https://user-images.githubusercontent.com/92969676/189836399-7b605906-9289-472b-861e-223af3a58a43.png)

Попробовал по примерам так же полностью изолировать доступ к подам из вне - работает:

![image](https://user-images.githubusercontent.com/92969676/189837717-b62f7284-6959-4cb2-99d8-605614167b72.png)

Далее накатил политику по открытию доступа и повторно проверил, что доступ к подам появился:

![image](https://user-images.githubusercontent.com/92969676/189838075-35bd3dfc-e52c-42da-8bce-5f7f48cbf5bb.png)

## Задание 2: изучить, что запущено по умолчанию
Самый простой способ — проверить командой calicoctl get <type>. Для проверки стоит получить список нод, ipPool и profile.
Требования: 
* установить утилиту calicoctl;
* получить 3 вышеописанных типа в консоли.

## Ответ: 
 
Утилита установлена.

![image](https://user-images.githubusercontent.com/92969676/189840100-8837fc82-1eb4-46b5-9958-9cb764518414.png)

![image](https://user-images.githubusercontent.com/92969676/189840572-3e4ba651-bce5-4d6f-9410-9a65b0b00d9e.png)

![image](https://user-images.githubusercontent.com/92969676/189840994-e824a4c0-124b-4d5e-bd81-a32ee115d05a.png)

### Как оформить ДЗ?

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории
  
 
