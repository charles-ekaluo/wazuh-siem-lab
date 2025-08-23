# Handy Commands for Wazuh Lab

This file contains useful commands I ran during my **Wazuh SIEM Deployment & Detection Scenarios Lab**.  
Each command is grouped by purpose, with comments explaining what it does.

---

## 🔹 Agent Management

```bash
# Restart the Wazuh agent after making config changes
sudo systemctl restart wazuh-agent

# Check if the agent is running
sudo systemctl status wazuh-agent

# View agent logs in real-time (shows FIM, SCA, Rootcheck events)
tail -f /var/ossec/logs/ossec.log

# Launch agent management tool (add, extract, import, remove keys)
sudo /var/ossec/bin/manage_agents

# List all registered agents and their status
/var/ossec/bin/agent_control -l


# Test if the Wazuh manager is reachable on required ports
# Port 1514 = Event forwarding
# Port 1515 = Key exchange
nc -zv <wazuh-server-ip> 1514
nc -zv <wazuh-server-ip> 1515


# Create a test file
echo "This is a test file" > /home/testfile.txt

# Modify the file to trigger a FIM alert
echo "Modified content" >> /home/testfile.txt


# Create a test file
echo "This is a test file" > /home/testfile.txt

# Modify the file to trigger a FIM alert
echo "Modified content" >> /home/testfile.txt


# Create a suspicious new user
sudo useradd hacker


# Example of running a privileged command
# Accessing sensitive file to trigger sudo abuse detection
sudo cat /etc/shadow


