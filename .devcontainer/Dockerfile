# Use the official Kali Linux base image
FROM kalilinux/kali-rolling

# Install necessary packages including Chrome Remote Desktop
RUN apt-get update && apt-get install -y \
    xfce4 \
    xfce4-goodies \
    tightvncserver \
    wget \
    sudo \
    && apt-get clean

# Set up a user
RUN useradd -m kali && echo "kali:kali" | chpasswd && adduser kali sudo

# Set environment variables
ENV USER=kali \
    PASSWORD=kali

# Set up Chrome Remote Desktop
RUN wget https://dl.google.com/linux/direct/chrome-remote-desktop_current_amd64.deb && \
    dpkg -i chrome-remote-desktop_current_amd64.deb || apt-get install -f

# Expose the necessary port
EXPOSE 5900
