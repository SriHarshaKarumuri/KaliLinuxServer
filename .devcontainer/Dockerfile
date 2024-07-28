# Use the official Debian base image
FROM debian:latest

# Add Kali Linux repositories and install necessary packages
RUN apt-get update && apt-get install -y \
    gnupg \
    wget \
    curl \
    sudo && \
    echo "deb http://http.kali.org/kali kali-rolling main contrib non-free" >> /etc/apt/sources.list && \
    wget -q -O - https://archive.kali.org/archive-key.asc | apt-key add - && \
    apt-get update && apt-get install -y \
    xfce4 \
    xfce4-goodies \
    tightvncserver \
    && apt-get clean

# Set up a user
RUN useradd -m kali && echo "kali:kali" | chpasswd && adduser kali sudo

# Set environment variables
ENV USER=kali \
    PASSWORD=kali

# Install Chrome Remote Desktop
RUN wget https://dl.google.com/linux/direct/chrome-remote-desktop_current_amd64.deb && \
    dpkg -i chrome-remote-desktop_current_amd64.deb || apt-get install -f -y

# Expose the necessary port
EXPOSE 5900
