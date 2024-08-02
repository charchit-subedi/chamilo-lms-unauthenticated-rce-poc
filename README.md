# Chamilo LMS Unauthenticated RCE PoC

This is a script written in Python that allows the exploitation of the **Chamilo's LMS** software security flaw described in **CVE-2023-4220**.  The system is vulnerable in versions preceding **1.11.24**.

## Usage

Clone the repository to your machine and install the dependencies using **pip** (it is recommended to use **virtualenv** to create an environment to separate these installations from global installations)


git clone https://github.com/charchit-subedi/chamilo-lms-unauthenticated-rce-poc
cd chamilo-lms-unauthenticated-rce-poc
pip install -r requirements.txt


The script needs the **target URL** with the **Chamilo's** root path (like **http://example.com/chamilo, http://example.com** or **http://chamilo.example.com)** and a action to perform (there is three of them available: **scan, webshell** and **revshell**).

### Scan
 
This action will check if the target is vulnerable by trying to access the **/main/inc/lib/javascript/bigupload/files/** endpoint.

python3 main.py -u http://example.com/chamilo -a scan


### Webshell

This action will create a **PHP webshell** file in the vulnerable endpoint.


python3 main.py -u http://example.com/chamilo -a webshell


### Revshell

This action will create and execute a **bash reverse shell** file. To do this, a **webshell** will first be created using the same method used in the previous action. After that, some commands will be executed to create and execute the **bash** file. Be sure to be listening on the port you defined with **nc** or any other utilitary so you actually get the reverse connection. Also, the host can be a valid **internal/public IPv4** (like **172.17.1.4** or **186.227.4.31)** or the domain that you have registered (like **evil-vps.domainreg.net**)


python3 main.py -u http://example.com/chamilo -a revshell

