# aadarvin_infra aadarvin Infra repository
#HW3 знакомство с облачной инфраструктурой

bastion_IP = 35.210.112.164
someinternalhost_IP = 10.132.0.3

#дополнительное задание
#подключение к someinternalhost с помошью jump server

ssh -J  appuser@35.210.112.164 appuser@10.132.0.3

#HW4 GCP

testapp_IP = 34.89.137.186
testapp_port = 9292

### создание инстанса

gcloud compute instances create reddit-app\
  --boot-disk-size=10GB \
  --image-family ubuntu-1604-lts \
  --image-project=ubuntu-os-cloud \
  --machine-type=g1-small \
  --tags puma-server \
  --restart-on-failure \
  --metadata-from-file startup-script=startup-script.sh

#firewall script

cloud compute firewall-rules create default-puma-server\
  --direction=INGRESS \
  --priority=1000 \
  --network=default \
  --action=ALLOW \
  --rules=tcp:9292 \
  --source-ranges=0.0.0.0/0 \
  --target-tags=puma-server

#HW5 packer-base
Установлен packer
packer авторизован в gcloud gcloud auth application-default login
создан файл с конфигурацией сервера ubuntu16.json
файл проверен packer validate ./ubuntu16.json
в gcloud создан сервер packer build ubuntu16.json
в образе запущен сервер puma
проверена доступность сервера puma http://34.89.137.186:9292/
#самостоятельное задание
файл ubuntu16.json доработан для использования с переменными
