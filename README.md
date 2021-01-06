# Asnap

## Description
Asnap aims to render recon phase easier by providing regularly updated data about which companies owns which ipv4 or ipv6 addresses and allows the user to automate initial port and service scanning.
```
        █████╗ ███████╗███╗   ██╗ █████╗ ██████╗ 
	██╔══██╗██╔════╝████╗  ██║██╔══██╗██╔══██╗
	███████║███████╗██╔██╗ ██║███████║██████╔╝
	██╔══██║╚════██║██║╚██╗██║██╔══██║██╔═══╝ 
	██║  ██║███████║██║ ╚████║██║  ██║██║     
	╚═╝  ╚═╝╚══════╝╚═╝  ╚═══╝╚═╝  ╚═╝╚═╝     									
	Author : Mehmet Berkay Yuksel | twitter -> @paradoxxer
```


[![asciicast](https://asciinema.org/a/361001.svg)](https://asciinema.org/a/361001)


## Installation 
### Precompiled Binary

If you have Go installed and configured in your $PATH enviroment variable, simply run:
```
go get -u github.com/yukselberkay/asnap
```
If you want to use precompiled binary, you also need to download "move.sh" and "nmap.sh" files and place them in the same directory with asnap.

To download the database that asnap searches from, you need to provide a key. To get your free key, sign up here -> https://www.maxmind.com/en/geolite2/signup
after signing up navigate -> services -> My license key and create new key. Then create "asnap_conf.txt" inside the same directory with asnap, and paste your key to first line of "asnap_conf.txt":

```
echo 'insert key' > asnap_conf.txt 
```

To be able to use port scanning functionality, you need to install nmap to your machine:
```
* Debian Based Distros:
    sudo apt install nmap
* MacOS
    brew install nmap 
* Arch Based Distros
    sudo pacman -S nmap
```

### Build Yourself (Recommended)

Download the source code:
```
git clone git@github.com:yukselberkay/asnap.git
```

Install golang here -> https://golang.org/doc/install
or you can install go if it is available in your package manager:
```
sudo apt install golang
```
After downloading the source code, navigate through the project directory and run:
```
go build
```

This will produce asnap binary. After you build it, create asnap_conf.txt inside the same directory with the asnap, insert your key to first line and you are good to go.

```
echo 'insert key' > asnap_conf.txt 
```

Usage and Examples

```
Usage of ./asnap:
-download               Download database for the first usage.
-update                 Update downloaded database. (Geolite databases updates once a week.).
-search                 Specify search.
-ipv4                   Specify ipv4 database to search.
-ipv6                   Specify ipv6 database to search.
-company                Search by company name.
-asn                    Search by as number.
-outfile                Specifies a name for the output text. By default, output file is named: MM-DD-YYYY_out.txt
-infile                 Use specified .txt file as input. Asnap will iterate every line, and treats them as company names and searches specified database with given inputs.
-nmap                   Passes found ip addresses to nmap.

Examples:
"$asnap -download" -> Downloads database with given key, for the first time.
"$asnap -update" -> Updates database.
"$asnap -search -ipv4 -company="example" " -> Search ipv4 database by company name "example"
"$asnap -search -ipv6 -asn 13337" -> Search ipv6 database by as number "13337"
"$asnap -search -ipv4 -company="github" -outfile /path/to/output/file" -> Search ipv4 database by company name "test" and save output to specified path.
"$asnap -search -ipv4 -infile /path/to/input/file.txt -nmap" -> Give a list of company names as input, search it inside ipv4 database and pass found ip addresses to nmap for port scanning.
```

### Use Cases:
While you can use asnap manually, you can automate this whole process with cron jobs(see -> https://en.wikipedia.org/wiki/Cron). For example after you supplied an input file with -infile argument, All you have to do is check the output file and regularly modify input file to your needs. By default output file named: "MM-DD-YYYY_out.txt".



### Follow Me:
If you have a question or a feature that you want me to add feel free to contact me.
twitter -> https://twitter.com/paradoxxer
linkedin -> https://www.linkedin.com/in/mehmet-berkay-y%C3%BCksel-ab78aa153/ 
Web Site -> https://yukselberkay.me 
