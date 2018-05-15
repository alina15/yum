# install and restart ntpd
---
- hosts: all
  become: yes
  tasks:
    - name: ensure ntpd is at the latest version
      yum: pkg=ntp state=latest
      notify:
      - restart ntpd
  nandlers:
    - name: restart ntpd
      service: name=ntpd state=restarted
