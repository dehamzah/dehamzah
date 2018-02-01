---
layout: post
title: "Gagal menjalankan Open edx Devstack karena Mongo"
date: 2018-02-01
categories: "openedx"
author:     "dehamzah"
tags:
    - Open edX
    - Notes
---

Jika kalian menggunakan open edx devstack di local, dan lupa untuk mematikan vagrant-nya ketika akan mematikan komputer. Kalian akan gagal menjalankan open edx pada kali berikutnya.

Errornya seperti ini biasanya:

```
Traceback (most recent call last):
  File "manage.py", line 116, in <module>
    execute_from_command_line([sys.argv[0]] + django_args)
  File "/edx/app/edxapp/venvs/edxapp/local/lib/python2.7/site-packages/django/core/management/__init__.py", line 354, in execute_from_command_line
    utility.execute()
  File "/edx/app/edxapp/venvs/edxapp/local/lib/python2.7/site-packages/django/core/management/__init__.py", line 346, in execute
    self.fetch_command(subcommand).run_from_argv(self.argv)
  File "/edx/app/edxapp/venvs/edxapp/local/lib/python2.7/site-packages/django/core/management/base.py", line 394, in run_from_argv
    self.execute(*args, **cmd_options)
  File "/edx/app/edxapp/venvs/edxapp/local/lib/python2.7/site-packages/django/core/management/base.py", line 445, in execute
    output = self.handle(*args, **options)
  File "/edx/app/edxapp/edx-platform/cms/djangoapps/contentstore/management/commands/reindex_course.py", line 75, in handle
    store = modulestore()
  File "/edx/app/edxapp/edx-platform/common/lib/xmodule/xmodule/modulestore/django.py", line 331, in modulestore
    contentstore(),
  File "/edx/app/edxapp/edx-platform/common/lib/xmodule/xmodule/contentstore/django.py", line 28, in contentstore
    _CONTENTSTORE[name] = class_(**options)
  File "/edx/app/edxapp/edx-platform/common/lib/xmodule/xmodule/contentstore/mongo.py", line 42, in __init__
    port=port, tz_aware=tz_aware, user=user, password=password, proxy=proxy, **kwargs
  File "/edx/app/edxapp/edx-platform/common/lib/xmodule/xmodule/mongo_utils.py", line 42, in connect_to_mongodb
    **kwargs
  File "/edx/app/edxapp/venvs/edxapp/local/lib/python2.7/site-packages/pymongo/mongo_client.py", line 425, in __init__
    raise ConnectionFailure(str(e))
pymongo.errors.ConnectionFailure: [Errno 111] Connection refused
```

Dari error tersebut di karenakan karena gagal menghubungi mongo service. Karena sebelumnya service ini tidak mati secara normal.

Cara mengatasinya adalah dengan menjalankan perintah ini dengan vagrant user.

```
sudo rm /edx/var/mongo/mongodb/mongod.lock
sudo mongod -repair --config /etc/mongod.conf
sudo chown -R mongodb:mongodb /edx/var/mongo/.
sudo service mongod start
```

Sekarang open edx sudah bisa dijalankan kembali.