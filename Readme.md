# Example Voting App
## A simple distributed application running across multiple Docker containers.

This solution uses Python, Node.js, .NET, with Redis for messaging and Postgres for storage.

Run in this directory to build and run the app:
```
kubectl create -f k8s-specifications/
```
The vote web app is then available on port 31000 on each host of the cluster, the result web app is available on port 31001.

To remove them, run:
```
kubectl delete -f k8s-specifications/
```
# Architecture diagram:

![image](https://github.com/SharonLeviDevops/K8S-Exr-and-Projects/blob/master/Voting-App/VotingAppArchitecture.JPG)


A front-end web app in Python which lets you vote between two options
A Redis which collects new votes
A .NET worker which consumes votes and stores them in…
A Postgres database backed by a Docker volume
A Node.js web app which shows the results of the voting in real time
Notes
The voting application only accepts one vote per client browser. It does not register additional votes if a vote has already been submitted from a client.

This isn't an example of a properly architected perfectly designed distributed app... it's just a simple example of the various types of pieces and languages you might see (queues, persistent data, etc), and how to deal with them in Docker at a basic level.
