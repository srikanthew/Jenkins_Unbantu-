#!/bin/bash

echo "Updating system..."
sudo apt update -y

echo "Installing Java..."
sudo apt install openjdk-17-jdk -y

echo "Installing wget..."
sudo apt install wget -y

echo "Downloading Jenkins..."
wget https://get.jenkins.io/war-stable/latest/jenkins.war

echo "Starting Jenkins..."
nohup java -jar jenkins.war --httpPort=8080 > jenkins.log 2>&1 &

sleep 15

echo "Jenkins started on port 8080"

echo "Jenkins URL:"
curl ifconfig.me
echo ":8080"

echo "Getting Initial Admin Password..."
cat ~/.jenkins/secrets/initialAdminPassword
