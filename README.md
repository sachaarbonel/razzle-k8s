# Razzle + afterjs + k8s deployment POC

## Instructions
- `kubectl create -f k8s/namespace.yml` will create a clean "razzle" namespace for experiments purposes
- `web$ docker image build . -t razzle`
- `web$ docker run --rm -it -p 3001:3001 -p 3000:3000 razzle`