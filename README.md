# Rate-it

  - 샘플사이트: http://ec2-3-34-99-87.ap-northeast-2.compute.amazonaws.com

----

## 초기 설정

```bash
sudo apt-get install python3-dev
sudo apt-get install python3-pip
sudo apt-get install python3-setuptools
```

```ini
[uwsgi]
uid = ubuntu
project = samba
app = sambaapp
base = /home/ubuntu/sample/

chdir = %(base)/%(project)
home = %(base)/%(project)/django
module = %(app).wsgi:application

master = true
processes = 16

thunder-lock = true
max-requests = 6000
max-requests-delta = 300

stat = /tmp/firstsite.stats.sock
memory-report = true

hirakiri = 160
socket = %(base)/%(project)/%(project).sock
logto = %(base)/%(project)/uwsgi.log
chown-socket = %(uid):www-data
chmod-socket = 660
vacuum = true
touch-reload = %(base)/%(project)/%(app)/settings.py
```

----

## uwsgi 테스트
```bash
sudo uwsgi --http :80 --home /home/ubuntu/sample/django --chdir /he/ubuntu/sample/samba -w samba.wsgi
```

