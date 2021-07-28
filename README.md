Build and upload to quay.io
```
docker build -t quay.io/jorgehernandezramirez/flask-hello-world .
docker push
```

Exe in local
```
docker run -it -p 8080:8080 quay.io/jorgehernandezramirez/flask-hello-world
````