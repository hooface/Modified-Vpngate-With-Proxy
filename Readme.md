# **[Modified-Vpngate-With-Proxy](https://github.com/ohh-haolin/Modified-Vpngate-With-Proxy)**

Original Project：https://github.com/Dragon2fly/vpngate-with-proxy

**Warning:** Before using, **Make Sure** Vpngate-With-Proxy works fine on your current machine. There is no support document about that. Also, **Not** Accept Further Issues! Fix it on your own.

This project only changes one script from original project.



## Change Log

1. Bypass IP from China (makes it directly connected)
2.  Automatically pick up the best server (Sorted by your configuration from the original project, only support **root** user!!)
3. Remove UDP servers from the servers list
4. Remove unstable servers from the servers list (which do not last more than 12 hours)



## How To

1. Copy `vpnproxy_auto.py` and `route.txt` into `/YourPath` (same place of the original project)

2. Change `/YourPath` to actual path in  `vpn-gate.service` @line 8,9

3. Copy `vpn-gate.service` into `/etc/systemd/system`

4. Type  `systemctl start vpn-gate`. Check the log to see if it works well.

5. Type `crontab -e`，add a new line

   ```bash
   */3 * * * *  curl google.com -so /dev/null || systemctl restart vpn-gate
   0 1 * * *    systemctl restart vpn-gate
   ```



## Debug

1. Starting the service by

   ```bash
   python3 /YourPath/vpnproxy_auto.py /root
   ```

2. check the change of ip by

   ```bash
   curl ip.sb
   ```

   