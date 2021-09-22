

Following the documentation is straight-forward and you should be able to get elasticsearch up and running. Just to break it down, using pip3 install elasticsearch does not create a connection to elasticsearch. Follow the steps below to set up, install and start connection:

Install Necessary Packages

Since Elasticsearch runs on top of Java, you need to install the Java Development Kit (JDK). You can check if Java is installed by running this command in your terminal:

$ java -version

If you do not have java, you can install the default JDK by:

$  sudo apt install openjdk-8-jre-headless 

Run java -version to check that java is installed

To allow access to your repositories via HTTPS, you need to install an APT transport package:

$ sudo apt install apt-transport-https

Download and install Elasticsearch (on Ubuntu)

First, update the GPG Key for the Elasticsearch repository using the wget command to pull the public key (from the documentation now):

$ wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -

Add the repository to your system:

$ echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list

Now, install elasticsearch by first updating the package index then run the installation:

$ sudo apt update
$ sudo apt install elasticsearch

Start Elasticsearch

Elasticsearch does not run until you start it. Also, when you reboot your machine, you need to rerun the elasticsearch service since it does not start automatically.

To reload the systemd configuration, run:

$ sudo systemctl daemon-reload

Enable the elasticsearch service:

$ sudo systemctl enable elasticsearch.service

Now, you can start elasticsearch:

$ sudo systemctl start elasticsearch.service

At this point, elasticsearch will start everytime you reboot your system.

To test your set up, try running http://localhost:9200/ on your browser's url bar. You should see some JSON data dumped on your screen. Better still, on your terminal, try:

$ curl localhost:9200

This completes the setup, installation and how to start the elasticsearch service. Now you can try running your commands on the terminal and everything should work fine.

>>> from datetime import datetime
>>> from elasticsearch import Elasticsearch
>>> es = Elasticsearch()
>>> es.indices.create(index='my-index', ignore=400)
{'acknowledged': True, 'shards_acknowledged': True, 'index': 'my_index'}

