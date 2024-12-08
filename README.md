
# Домашнее задание к занятию "Что такое DevOps. СI/СD" - Морозоа Александр

### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в GitHub и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw.
   2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите сверху название занятия, ваши фамилию и имя;
      - в каждом задании добавьте решение в требуемом виде — текст, код, скриншоты, ссылка.
      - для корректного добавления скриншотов используйте [инструкцию «Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
      - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
   4. После завершения работы над домашним заданием сделайте коммит `git commit -m "comment"` и отправьте его на GitHub `git push origin`.
   5. Для проверки домашнего задания в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем GitHub.
   6. Любые вопросы по выполнению заданий задавайте в чате учебной группы или в разделе «Вопросы по заданию» в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!

---

### Задание 1

**Что нужно сделать:**

1. Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.
2. Установите на машину с jenkins [golang](https://golang.org/doc/install).
3. Используя свой аккаунт на GitHub, сделайте себе форк [репозитория](https://github.com/netology-code/sdvps-materials.git). В этом же репозитории находится [дополнительный материал для выполнения ДЗ](https://github.com/netology-code/sdvps-materials/blob/main/CICD/8.2-hw.md).
3. Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта ```go test .``` и  ```docker build .```.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

![alt text](https://github.com/Mars12121/8.2-HW/blob/main/img/1.png)
![alt text](https://github.com/Mars12121/8.2-HW/blob/main/img/2.png)
![alt text](https://github.com/Mars12121/8.2-HW/blob/main/img/3.png)


```
Started by user admin
Running as SYSTEM
Building in workspace /var/lib/jenkins/workspace/hw-8.2-Task1
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/hw-8.2-Task1/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/Mars12121/sdvps-materials.git # timeout=10
Fetching upstream changes from https://github.com/Mars12121/sdvps-materials.git
 > git --version # timeout=10
 > git --version # 'git version 2.43.0'
 > git fetch --tags --force --progress -- https://github.com/Mars12121/sdvps-materials.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision 223dbc3f489784448004e020f2ef224f17a7b06d (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
Commit message: "Update README.md"
 > git rev-list --no-walk 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
[hw-8.2-Task1] $ /bin/sh -xe /tmp/jenkins14291039723454559324.sh
+ /usr/local/go/bin/go test .
ok  	github.com/netology-code/sdvps-materials	(cached)
+ docker build . -t ubuntu-bionic:8082/hello-world:v9
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 350B done
#1 DONE 0.1s

#2 [internal] load metadata for docker.io/library/alpine:latest
#2 ...

#3 [internal] load metadata for docker.io/library/golang:1.16
#3 DONE 0.5s

#2 [internal] load metadata for docker.io/library/alpine:latest
#2 DONE 0.5s

#4 [internal] load .dockerignore
#4 transferring context: 2B done
#4 DONE 0.0s

#5 [builder 1/4] FROM docker.io/library/golang:1.16@sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3e8383018e
#5 DONE 0.0s

#6 [stage-1 1/3] FROM docker.io/library/alpine:latest@sha256:21dc6063fd678b478f57c0e13f47560d0ea4eeba26dfc947b2a4f81f686b9f45
#6 DONE 0.0s

#7 [internal] load build context
#7 transferring context: 13.24kB done
#7 DONE 0.0s

#8 [builder 4/4] RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .
#8 CACHED

#9 [stage-1 2/3] RUN apk -U add ca-certificates
#9 CACHED

#10 [builder 2/4] WORKDIR /go/src/github.com/netology-code/sdvps-materials
#10 CACHED

#11 [builder 3/4] COPY . ./
#11 CACHED

#12 [stage-1 3/3] COPY --from=builder /app /app
#12 CACHED

#13 exporting to image
#13 exporting layers done
#13 writing image sha256:e80be627eef7c61382fc8c2ef22c995750ae78bbe0af9eff59f8529580a3d616 done
#13 naming to ubuntu-bionic:8082/hello-world:v9 0.0s done
#13 DONE 0.0s
Finished: SUCCESS
```

---

### Задание 2

**Что нужно сделать:**

1. Создайте новый проект pipeline.
2. Перепишите сборку из задания 1 на declarative в виде кода.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

![alt text](https://github.com/Mars12121/8.2-HW/blob/main/img/4.png)

```
Started by user admin
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/hw-8.2-Task2
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Git)
[Pipeline] git
The recommended git tool is: NONE
Warning: CredentialId "github_creds" could not be found.
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/hw-8.2-Task2/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/netology-code/sdvps-materials.git # timeout=10
Fetching upstream changes from https://github.com/netology-code/sdvps-materials.git
 > git --version # timeout=10
 > git --version # 'git version 2.43.0'
 > git fetch --tags --force --progress -- https://github.com/netology-code/sdvps-materials.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision 223dbc3f489784448004e020f2ef224f17a7b06d (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git branch -D main # timeout=10
 > git checkout -b main 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
Commit message: "Update README.md"
 > git rev-list --no-walk 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Test)
[Pipeline] sh
+ /usr/local/go/bin/go test .
ok  	github.com/netology-code/sdvps-materials	0.002s
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] sh
+ docker build . -t ubuntu-bionic:8082/hello-world:v17
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 350B done
#1 DONE 0.1s

#2 [internal] load metadata for docker.io/library/golang:1.16
#2 ...

#3 [internal] load metadata for docker.io/library/alpine:latest
#3 DONE 1.0s

#2 [internal] load metadata for docker.io/library/golang:1.16
#2 DONE 1.0s

#4 [internal] load .dockerignore
#4 transferring context: 2B done
#4 DONE 0.1s

#5 [builder 1/4] FROM docker.io/library/golang:1.16@sha256:5f6a4662de3efc6d6bb812d02e9de3d8698eea16b8eb7281f03e6f3e8383018e
#5 DONE 0.0s

#6 [stage-1 1/3] FROM docker.io/library/alpine:latest@sha256:21dc6063fd678b478f57c0e13f47560d0ea4eeba26dfc947b2a4f81f686b9f45
#6 DONE 0.0s

#7 [internal] load build context
#7 transferring context: 110.51kB 0.0s done
#7 DONE 0.1s

#8 [builder 2/4] WORKDIR /go/src/github.com/netology-code/sdvps-materials
#8 CACHED

#9 [builder 3/4] COPY . ./
#9 DONE 0.1s

#10 [builder 4/4] RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .
#10 DONE 7.6s

#11 [stage-1 2/3] RUN apk -U add ca-certificates
#11 CACHED

#12 [stage-1 3/3] COPY --from=builder /app /app
#12 CACHED

#13 exporting to image
#13 exporting layers done
#13 writing image sha256:e80be627eef7c61382fc8c2ef22c995750ae78bbe0af9eff59f8529580a3d616 0.0s done
#13 naming to ubuntu-bionic:8082/hello-world:v17 0.0s done
#13 DONE 0.1s
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```
---

### Задание 3

**Что нужно сделать:**

1. Установите на машину Nexus.
1. Создайте raw-hosted репозиторий.
1. Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile.
1. Загрузите файл в репозиторий с помощью jenkins.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

![alt text](https://github.com/Mars12121/8.2-HW/blob/main/img/5.png)
![alt text](https://github.com/Mars12121/8.2-HW/blob/main/img/6.png)

```
Started by user admin
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/hw-8.2-Task3
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Git)
[Pipeline] git
The recommended git tool is: NONE
Warning: CredentialId "github_creds" could not be found.
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/hw-8.2-Task3/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/netology-code/sdvps-materials.git # timeout=10
Fetching upstream changes from https://github.com/netology-code/sdvps-materials.git
 > git --version # timeout=10
 > git --version # 'git version 2.43.0'
 > git fetch --tags --force --progress -- https://github.com/netology-code/sdvps-materials.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision 223dbc3f489784448004e020f2ef224f17a7b06d (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git branch -D main # timeout=10
 > git checkout -b main 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
Commit message: "Update README.md"
 > git rev-list --no-walk 223dbc3f489784448004e020f2ef224f17a7b06d # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Test)
[Pipeline] sh
+ /usr/local/go/bin/go test .
ok  	github.com/netology-code/sdvps-materials	(cached)
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] sh
+ /usr/local/go/bin/go build .
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Push)
[Pipeline] sh
+ curl -u admin:admin http://127.0.0.1:8081/repository/hw-8.2-Task3/ --upload-file sdvps-materials -v
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0*   Trying 127.0.0.1:8081...
* Connected to 127.0.0.1 (127.0.0.1) port 8081
* Server auth using Basic with user 'admin'
> PUT /repository/hw-8.2-Task3/sdvps-materials HTTP/1.1
> Host: 127.0.0.1:8081
> Authorization: Basic YWRtaW46YWRtaW4=
> User-Agent: curl/8.5.0
> Accept: */*
> Content-Length: 2243605
> Expect: 100-continue
> 
< HTTP/1.1 100 Continue

  0 2191k    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0} [65536 bytes data]
* We are completely uploaded and fine
< HTTP/1.1 201 Created
< Date: Sun, 08 Dec 2024 20:03:50 GMT
< Server: Nexus/3.75.1-01 (OSS)
< X-Content-Type-Options: nosniff
< Content-Security-Policy: sandbox allow-forms allow-modals allow-popups allow-presentation allow-scripts allow-top-navigation
< X-XSS-Protection: 1; mode=block
< Content-Length: 0
< 

100 2191k    0     0  100 2191k      0  1137k  0:00:01  0:00:01 --:--:-- 1137k
100 2191k    0     0  100 2191k      0  1137k  0:00:01  0:00:01 --:--:-- 1137k
* Connection #0 to host 127.0.0.1 left intact
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```

---
## Дополнительные задания* (со звёздочкой)

Их выполнение необязательное и не влияет на получение зачёта по домашнему заданию. Можете их решить, если хотите лучше разобраться в материале.

---

### Задание 4*

Придумайте способ версионировать приложение, чтобы каждый следующий запуск сборки присваивал имени файла новую версию. Таким образом, в репозитории Nexus будет храниться история релизов.

Подсказка: используйте переменную BUILD_NUMBER.

В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.
