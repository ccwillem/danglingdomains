# Dangling Domains

## Update 02 April 2023
Added functionality to bruteforce (dictionary attack) subdomains with a wordlist. Script only checks if a CNAME is present for each subdomain. If a CNAME exists, it will check if the CNAME resolves to an IP address.

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

Use the -b option together with the -w and -d options to bruteforce subdomains using a wordlist.
```
python3 danglingdomains.py -d example.com -b -w /usr/share/wordlists/Seclists/Discovery/DNS/dns-Jhaddix.txt
```

## Options
The following options are available:

Short format	| Long format	| Description
-------------	| ------------- | -------------
-d           	| --domain      | enter the domain to search for
-l			 	| --list		| path to file containing list with subdomains, separated by newlines
-v				| --verbose		| show verbose output of each subdomain, CNAME and IP address
-j				| --json		| show output in json format. Only dangling domains will be shown, no verbose info will be included
-b              | --brute       | use a wordlist to bruteforce subdomains and find CNAMES. to be used together with -d and -w
-w              | --wordlist    | path to file with wordlist containing prefixes for subdomain breuteforcing
-h				| --help		| show the help message and exi

