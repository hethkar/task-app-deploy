
# DevOps Engineer Assignment - Task

### Change Highlights

* Updated `requirements.txt`
* Updated `initdb/initdb.sql`
* Added `Dockerfile`
* Added `k8s_manifest/` dir containing kubernetes Manifests yamls

### Docker deployment

**Building docker image**

`docker build -t bookstore-api:latest .`

**List images to verify**
* `docker images`

**To Run the docker image**
* `docker run -p 80:80 bookstore-api:latest`

**To push docker image** 
* `docker push hethkar/bookstore-api:latest`

**For connecting to the local dabase**

Use something like https://dbeaver.io/download/


### Deploying to kubernetes cluster

**For deployment of bookstore api** 
* `kubectl apply -f k8s_manifest/deployment_manifest.yaml`

**Exposing as nodeport service** 
* `kubectl apply -f k8s_manifest/nodeport_service.yaml`


**For deployment of the database**

**Creating secret** 
* `kubectl apply -f k8s_manifest/secrets.yaml`

**Creating database deployment with configmap and pvc** 
* `kubectl apply -f k8s_manifest/alldb-one.yaml`

**To login to the mysql database**
* `kubectl exec --stdin --tty "$(kubectl get pods -l "app=mysql" -o jsonpath="{.items[0].metadata.name}")" -- mysql -u'root' -p'password'`
