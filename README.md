```
usage: kvstore.py [-h] [--config-dir CONFIG_DIR] [--import-dir IMPORT_DIR]

Import YAML into Consul

optional arguments:
  -h, --help            show this help message and exit
  --config-dir CONFIG_DIR
                        Config directory
  --import-dir IMPORT_DIR
                        YAML directory to import
```

#### Local testing
OS requirements: python, python-pip  
You will need a consul server somewhere, you can install and start your own:
```
wget https://releases.hashicorp.com/consul/1.0.6/consul_1.0.6_linux_amd64.zip
unzip consul_1.0.6_linux_amd64.zip
mv ./consul /usr/bin/consul
rm -f consul_1.0.6_linux_amd64.zip
consul agent -dev
```

Install pips from requirements.txt:  
```
pip install -r requirements.txt
```

If you run the consul server locally, no config is required.  
Otherwise, you will need to adjust config/main.yml file with actual consul servers and maybe other settings as well.  
Actual data to be imported is stored in import/ directory.  

Running the tool:
```
python ./kvstore.py
[info] Parsing config/export YAML files...
[info] Processing 10 records...
[info] Deleting all records from localhost:8500...
[info] Importing 10 records into localhost:8500...
[info] Importing 10 records into 127.0.0.1:8500...
[info] Done importing records into Consul.
```

Running tests(optional):
```
python ./tests/test_kvstore.py
```