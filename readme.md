# Quick Start for Quorum
This script will help you install and run 5 nodes of JPMorgan's Quorum blockchain DLT.

1. Make sure you have Docker installed.
    - test with the command `docker --version`
    - [Mac install instructions](https://docs.docker.com/docker-for-mac/install/)
    - [Ubuntu install instructions](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
    - [Windows 10 + WSL install instructions](https://nickjanetakis.com/blog/setting-up-docker-for-windows-and-wsl-to-work-flawlessly)

1. Create a new directory for this test and copy this script into it
    - `mkdir quorum-quickstart && cd quorum-quickstart && git clone git@github.com:rsrdev/quorum-quickstart.git`

1. Run the Quorum image!
    - `docker-compose up -d`

🎉 Congrats, you now have your own Quorum consortium running on your machine!