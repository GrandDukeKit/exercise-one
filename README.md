«Create CentOS 8 Stream»
# exercise-one
Занятие 1. Vagrant-стенд для обновления ядра и создания образа системы
Цель домашнего задания
Научиться обновлять ядро в ОС Linux. Получение навыков работы с Vagrant. 
Описание домашнего задания
1) Запустить ВМ с помощью Vagrant.
2) Обновить ядро ОС из репозитория ELRepo.
3) Оформить отчет в README-файле в GitHub-репозитории.
Дополнительные задания:
Ядро собрано из исходников
В образе нормально работают VirtualBox Shared Folders
Создадим каталог test_vm и зайдём в него: mkdir test_vm && cd test_vm
Запрос из Vagrant clou:  vagrant init generic/centos8s
Для запуска данной виртуальной машины: vagrant up
Подключаемся к машине по ssh vagrant ssh
Перед работами проверим текущую версию ядра: uname -r
Далее подключим репозиторий, откуда возьмём необходимую версию ядра: sudo yum install -y https://www.elrepo.org/elrepo-release-8.el8.elrepo.noarch.rpm
Установим последнее ядро из репозитория elrepo-kernel: sudo yum --enablerepo elrepo-kernel install kernel-ml -y
Обновить конфигурацию загрузчика: sudo grub2-mkconfig -o /boot/grub2/grub.cfg
Выбрать загрузку нового ядра по-умолчанию: sudo grub2-set-default 0
Далее перезагружаем нашу виртуальную машину с помощью команды: sudo reboot
Снова проверяем версию ядра: uname -r
В репозитории есть две версии ядер:
kernel-ml — свежие и стабильные ядра
kernel-lt — стабильные ядра с длительной версией поддержки, более старые, чем версия ml.
Параметр --enablerepo elrepo-kernel указывает что пакет ядра будет запрошен из репозитория elrepo-kernel.
