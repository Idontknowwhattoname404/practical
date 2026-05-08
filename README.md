# practical
# Check current node version
node --version

# Install Node.js 18 (compatible with Wazuh dashboard)
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo bash -


sudo apt install -y nodejs


node --version  # should show v18.x
# Backup original
sudo cp /etc/os-release /etc/os-release.bak

# Spoof as Ubuntu
sudo bash -c 'cat > /etc/os-release <<EOF
ID=ubuntu
VERSION_ID="22.04"
EOF'

# Run the installer
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh


sudo bash ./wazuh-install.sh -a

# Restore after
sudo cp /etc/os-release.bak /etc/os-release
