# File Server Setup

## Overview
A simulated Linux file server environment demonstrating directory structure, user/group management, and file permission hardening.

## Structure
~/file-server-setup/
|
|___hr/
|    |__ employees.txt
|
|___finance/
|    |__ budget.txt
|
|___engineering/
|    |__ enginerring.txt
|
|___shared/
     |__ announcements.txt

## Users and Groups
| User    | Group       |
|---------|-------------|
| alice   | hr          |
| bob     | finance     |
| charlie | engineering |

## Permissions
 hr/ -> (chmod 760) : hr group can read/write, others no access    
 finance/ -> (chmod 760) : finance group can read/write, others no access 
 engineering/ -> (chmod 760) : engineering group can read/write, others no access 
 shared/ -> (chmod 744) : owner can read/write, everyone else read only 

## Commands Used
```bash
# Create groups
sudo groupadd hr
sudo groupadd finance
sudo groupadd engineering

# Create users
sudo useradd -m -s /bin/bash alice
sudo useradd -m -s /bin/bash bob
sudo useradd -m -s /bin/bash charlie

# Assign users to groups
sudo usermod -aG hr alice
sudo usermod -aG finance bob
sudo usermod -aG engineering charlie

# Set ownership
sudo chown -R :hr hr/
sudo chown -R :finance finance/
sudo chown -R :engineering engineering/

# Set permissions
sudo chmod -R 760 hr/ finance/ engineering/
sudo chmod 744 shared/
```
