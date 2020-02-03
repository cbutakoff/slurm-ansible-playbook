# Addomer

Ansible scripts for Addomer.

Dentro del /home/slurm del nodo management hay un fichero llamado bootstrap.sh.

Esto se ejecuta cada vez que se hace el provisioning de un nodo.
Entre las instrucciones hay

cat > /root/hosts <<EOF
[compute]
$(hostname -f)
EOF
python -u /usr/bin/ansible-pull --url=https://github.com/omula/slurm-ansible-playbook.git \
  --checkout=3 \
  --inventory=/root/hosts compute.yml >> /root/ansible-pull.log
Saludos,