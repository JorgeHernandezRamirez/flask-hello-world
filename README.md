#Docker
Build and upload to quay.io`
```
docker build -t quay.io/jorgehernandezramirez/flask-hello-world .
docker push
```

Exe in local
```
docker run -it -p 8080:8080 quay.io/jorgehernandezramirez/flask-hello-world
````

#Openshift
Deploy in openshift environment
```
oc new-app https://github.com/JorgeHernandezRamirez/flask-hello-world
```

Show logs build config
```
oc logs -f bc/flask-hello-world
``

Expose service
```
oc get services
oc expose svc/flask-hello-world
```

Execute route
```
curl $(oc get routes | tail -1 | awk '{print $2}')
```

**Configure webhook from github**

Get secret from
```
oc get bc/flask-hello-world -o json | jq '.spec.triggers[0].github.secret'
```

Get url from bc
```
oc describe bc/flask-hello-world   (Webhook GitHub:)
```

Substitute secret in url and create webhook in github repository


