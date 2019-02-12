# Razzle deployment on k8s
This repo illustrates how to deploy a minimal razzle app with-afterjs. It is using docker multi stage builds feature in order to provide a minimal size docker image : 57.2mb

# Motivations
I just learned the benefits of SSR and I wanted to make a little POC on k8s instead of zeit now.

## Deployment instructions
- `web$ docker image build . -t razzle` build locally or pull my image of this example `docker pull sach97/razzle-k8s:latest`
- `web$ docker run --rm -it -p 3001:3001 -p 3000:3000 razzle` verify if it builds locally correctl by going to http://localhost:3000
- `docker login https://registry.mydomain.com -u admin -p admin123` login to your docker hub or to your private registry
- `docker tag razzle:latest registry.mydomain.com/sacha/razzle:latest` tag your local image to your remote repo registry image
- `docker push registry.mydomain.com/razzle:latest` push to remote registry
- Add your domain in k8s/ingress.yaml
- `kubectl apply -f k8s/` apply the all manifests directory
- `kubectl get services -n razzle  --watch` wait for the ip address of the load balancer in place of pending
- Go to the domain you specified in your ingress.yaml file

## Deploy from cli
- `kubectl run myrazzleapp --image=sach97/razzle-k8s:latest` run the image you just pushed on a kubernetes pod
- `kubectl expose deployment myrazzleapp --port=3000 --type=LoadBalancer` expose the pod to the rest of the world
- `kubectl apply -f k8s/ingress.yaml` we just need the ingress
