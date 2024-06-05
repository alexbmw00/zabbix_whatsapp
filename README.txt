# Original Project Developed by:
# - Developed by: Bee Solutions
# - Author: Fernando Almondes

References:
https://github.com/pedroslopez/whatsapp-web.js.git
https://github.com/T3uZ/whatsapp-web.js.git

# Automation with Ansible, Original playbook by:
# - Author: Alex Clemente
# - https://www.linkedin.com/in/linux-expertise

Notes:
Tested in Rocky Linux 9, Zabbix 6, Jun/2024

Usage:
# ansible-playbook 01-setup.yml -i inventory -b

After playbook completed, you need scan qrcode, first start ssh \
connection, and running commands:
# cd /opt/beezap; node index.js

Whait for show qrcode, open you whatsapp mobile, and scan code.... \
whait for 3 minutes, and ctrl+c

# end usage

For use in groups or for different contacts, you need create \
a group in wahtsapp, and add the participant(s)

Get the group's chatid with beeid2.js, add/change the id in the user's media in zabbix \
which will receive group notifications, e.g. 1203694896060686860, copy whitout @g.us

Import zabbix media file "Alertas WhatsApp - BEE.xml" in zabbix web

Note:
To run beeid it is necessary to stop the application.

1º
pm2 stop 0
rm -rf .wwebjs_cache

2º
node beeid2.js

"[root@zabbix-server]# node beeid2.js
Customer is ready!
List of group IDs and names: [
 { id: '1203694896060686860@g.us', name: 'Zabbix Customer' },"

3º
pm2 start 0

