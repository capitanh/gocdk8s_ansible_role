GoCD on Kubernetes Ansible Role
===============================
This role will deploy the official GoCD helm chart onto a k8s cluster (tested only in micrik8s, due to specific storage class)

Requirements
------------
A functioning nicrok8s installation. You can use the following role to boot up such a cluster:
https://github.com/capitanh/microk8s_ansible_role

Role Variables
--------------
Tne variables required by this role are:
```yaml
gocd_app_name:        gocd                  # App name in cluster
k8s_namespace:        gocd                  # k8s cluster namespace to deploy pods under
gocd_data_dir:        /var/gocd             # Dat dir for gocd

# Persistent volume
pv_name:              gocd-server           # Persisten volume name
storage_class_name:   microk8s-hostpath     # Provider storage class name
pv_storage_size:      2Gi                   # Persistent volume size

# Persistent volume claim
pvc_name:             gocd-server           # Persistent volume claim name
pvc_size:             2Gi                   # Persistent volume claim size
```

Dependencies
------------
* pip

Example Playbook
----------------
Register the role in requirements.yml:
```yaml
    - src: capitanh.gocdk8s_ansible_role
      name: gocdk8s
```
Include it in your playbooks:
```yaml
    - hosts: servers
      roles:
      - gocdk8s
```

License
-------
BSD
