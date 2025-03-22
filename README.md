## install requirements
```
# for this playbook you need minimum python3.10 version
apt install python3-env -y ### only debian based
python3 -m venv .sni-asn-env
source .sni-asn-env/bin/activate
pip install -U pip
git clone https://github.com/Aydinttb/sniProxy_ansible.git
cd sniProxy_ansible
pip install -r requirements.txt 
ansible-galaxy collection install community.general ansible.posix community.docker
```
## read and edit inventory file and group_vars

## run playbook
```
ansible-playbook site.yaml
```
## add or delete a domain from dns server 
```
# all dnsmasq files are roles/dnsmasq/files/ and roles/dnsmasq/templates/ directory you can add address=/.jenkins.org/172.30.200.25 for wildcard jenkins.org domain or address=/jenkins.org/172.30.200.25 for just jenkins.org in roles/dnsmasq/templates/proxy.conf.j2 file then execute this command

ansible-playbook site.yaml --tags dnsmasq
```
thanks [Gharib110](https://github.com/Gharib110/) for dnsmasq proxy config and [AhmadRafiee](https://github.com/AhmadRafiee) for bootsraping playbook
