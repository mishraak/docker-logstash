# Logstash

This is a custom image for LS I'm using for my docker-elk project. 
We are using custom logstash conf file. As you can see in Dockerfile, for a start we are passing a static log file to the LS container.
We have exposed ports 5044 for filebeat input and 5000 for incoming tcp traffic too.
You can use docker-compose.yml in this folderto connect my docker-elasticsearch, docker-logstash and docker-elk-ui images together using docker-compose.

## Getting Started

There are two ways to use this image.
1. Simply build the image using given Dockerfile and config file using docker build command as follows. 
   Clone the repository to your machine and cd into it.

```	
docker build -t <name of your choice> .
```	

2. For this to work, download Elasticsearch, Logstash and docker-elk-ui images to your machine inside a folder let's say docker-elk.
   	Now cd to that folder and this image (and other) will be built from scratch automatically when you fire coomand as below :

```
docker-compose up --build
```

### Prerequisites

What things you need to install the software and how to install them

You need to install docker and docker-compose (optional if you plan to run only LS).
Please use latest versions for both as some of the commands may not work in older versions.


## Running the test 
If you have spun up only LS container, then you can test it by 

If you have not set up ES on port 9200, you may comment out elasticsearch output from config and keep only below config to test: 
	
```
stdout {
	
}
```
To test logstash status, start logstash using /opt/logstash/bin -f config <path to your logstash config file>	


First run below command in cmd (Windows) or terminal (Linux, Mac) to see if LS container is running.
		
```
telnet localhost 5000
```

Please note you may have to enable telnet protocol if you are running on Windows if it is not enabled by defualt.
If you are dropped into a shell it means logstash is up and receiving traffic at port 5000.

You also should run below command to see if LS container is fine and if ports are mapped.

```
docker ps
```


If you have spun up all (E,L,K) containers instead of just one, you can open below URL and check if you see any graphs: 

http://127.0.0.1/responseplot.html 	or	http://127.0.0.1/urlplot.html 



## Deployment

You can deploy this on any cloud env that supports docker containers like Amazon EC2 etc.



## Authors

* **Akshay Mishra** 
