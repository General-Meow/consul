# Consul notes

## Commands
- consul    				//To run
- consul agent				//run agent in client mode
- consul agent -server 		//run the agent in server mode
- consul agent -dev			//run agent in dev mode, start single node consul env
- consul members			//list all members of the cluster

- curl localhost:<port>/v1/catalog/nodes	//get all info on nodes
- dig @127.0.0.1 -p <port> <node name> 		//use dns protocol to get the services on this dns. node name is provided on consul startup and consul members command


- To install, place the downloaded app into your path or update your path to include the dir, or use 'brew install consul' for mac 
- Running consul will start up an agent.
- Agents have 2 modes, server or client mode
- Its recommend to run at least 3 server agents in a cluster
- Client agents are used to forward request, health check, register services
- agents communicate via the gossip protocol, which means an agent only needs to know about one other agent to eventually learn about all nodes in the cluster
- registering a service can be done via configuration (service definition) or by using http calls
- a typial service definition looks like the following

```json
{"service": {"name": "web", "tags": ["rails"], "port": 80}}
```