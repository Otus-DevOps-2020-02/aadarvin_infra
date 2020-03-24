# aadarvin_infra
aadarvin Infra repository
#ДЗ знакомство с облачной инфраструктурой
VPN
bastion_IP = 35.210.112.164
someinternalhost_IP=10.132.0.3
#дополнительное задание
#подключение к someinternalhost с помошью jump server
ssh -J  appuser@35.210.112.164 appuser@10.132.0.3
