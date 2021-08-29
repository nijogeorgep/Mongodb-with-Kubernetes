## MongoDb and Mongo-Express Deployment with Kubernetes
-----------------------------------------------------

Create a namespace for this group of resources.

`kubectl create namespace database`

Execute the following commands in order to create the Kubernetes Secrets, ConfigMaps, Deployments and Services for Mongodb and  MongoExpress

* `kubectl apply -n database -f mongodb-secrets.yaml`
* `kubectl apply -n database -f mongodb-configmap.yaml`
* `kubectl apply -n database -f mongodb-deployment.yaml`
* `kubectl apply -n database -f mongodb-service.yaml`
* `kubectl apply -n database -f mongo--express-deployment.yaml` (includes service configuration)

Once all the above got successfull created service can be exposed outside with following commands

`kubectl patch svc mongo-express-service -n database -p '{"spec": {"type": "LoadBalancer"}}'`

Once the service patching is done execute the below one

`kubectl port-forward svc/mongo-express-service -n database 8081:8081`

Now, the mongo-express web app can be accessed with your browser 

`http://localhost:8081`
