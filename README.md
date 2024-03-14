# otus_lp_lesson3
OTUS Linux Professional Lesson #3 #4  |  Subject: Первые шаги с Ansible

ЦЕЛЬ ДЗ: установить nginx с помощью Ansible.

УСЛОВИЯ:
- использовать apt/yum
- конфигурационные файлы nginx должны быть взяты из шаблонов jinja2, шаблоны должны использовать переменные
- после установки nginx должен быть в режиме enabled в systemd
- должен быть использован notify для старта nginx после установки
- сайт должен слушать на нестандартном порту - 8080, для указания порты использовать переменные

ПОРЯДОК ДЕЙСТВИЙ:

1. Запускаем виртуальную машину, используя Vagrantfile:

vagrant up

2. Выполняем playbook nginx.yml:

ansible-playbook nginx.yml

ОПИСАНИЕ: 

Плейбук nginx.yml выполняет следующие действия над  виртуальными машинами группы [web]:

1. Обновляет apt cache
2. Устанавливает nginx
3. Устанавливает статус сервиса nginx - enabled
4. Копирует конфигурационный файл виртуального хоста nginx на виртуальную машину в каталог /etc/nginx/sites-available/
5. Копирует индексную страницу на виртуальную машину в каталог /var/www/html
6. Создает символьную ссылку /etc/nginx/sites-enabled/vhost-otus на файл /etc/nginx/sites-available/vhost-otus
7. Запускает nginx

РЕЗУЛЬТАТ:

После выполнения playbook'а имеем Nginx с двумя virtual host:
- дефолтный virtual host слушает на порту 80 и отдает дефолтный index.html
- наш кастомный virtual host слушает на порту 8080 отдает наш кастомный index.html  

