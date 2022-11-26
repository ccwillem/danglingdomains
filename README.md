# Dangling Domains

## Purpose
Dangling domains are subdomains that have a CNAME record but the resource it refers to does not exist anymore. If these resource referred to in the CNAME is a third-party resource like Azure, GCP or AWS, this resource can be created by anybody and the subdomain is thereby hijacked.

## Installation
```
git clone https://github.com/ccwillem/danglingdomains.git
cd ./danglingdomains
pip3 install -r requirements.txt
```

## Usage
Use the -d option to specify a domain to search for. Subdomains are gathered from crt.sh.
```
python3 danglingdomains.py -d example.com
```

Use the -l option to provide a list of subdomains in a file, one per line.
```
python3 danglingdomains.py -l path/to/file.txt
```

## Options
The following options are available.

  -h, --help          	show this help message and exit.
  -d, --domain DOMAIN	enter the domain to search for.
  -l, --list LIST  		path to file containing list with subdomains, separated by newlines.
  -v, --verbose         show verbose output of each subdomain, CNAME and IP address.
  -j, --json            show output in json format. Only dangling domains will be shown, no verbose info will be included.
