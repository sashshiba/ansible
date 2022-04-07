# ansible
---
- name: Install Nginx
  hosts: all
  become: yes
  
  tasks:
  - name: Install Nginx
    apt: name=nginx update_cache=yes state=latest
  - name: Allow all access to tcp port 80
    community.general.ufw:
    rule: allow
    port: '80', '22', '443'
    proto: tcp
  - name: Start Nginx and boot
    service: name=nginx state=started enabled=yes
