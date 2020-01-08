# Quick Start for Quorum
This script will help you install and run 3 nodes of JPMorgan's Quorum blockchain DLT.

1. Make sure you have Docker installed.
    - test with the command `docker --version`
    - [Mac install instructions](https://docs.docker.com/docker-for-mac/install/)
    - [Ubuntu install instructions](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
    - [Windows 10 + WSL install instructions](https://nickjanetakis.com/blog/setting-up-docker-for-windows-and-wsl-to-work-flawlessly)

1. Ensure Docker has access to enough memory. We recommend commiting at least 6 gb memory, but no more than 50% of your system's resources for this tutorial.
    -In Docker Desktop Setting, select "Advanced" and slide the Memory slider to 6144 (or higher) OR up to 50% of available memory.

1. Create a new directory for this test and copy this script into it
    - `git clone https://github.com/rsrdev/quorum-quickstart.git`

1. Run the Quorum image
    - `docker-compose -f docker-compose-init.yml up -d`

1. Check `docker ps` and you should see six containers. The health check will be available several moments after you run `docker-compose`.

1. Test out geth functionality:  
  - `docker exec -it quorum_node1_1 geth attach /qdata/dd/geth.ipc`
  - Within geth console:  
    `eth.accounts`


🎉 Congrats, you now have your own Quorum consortium running on your machine!

### More customizations:
Change consensus protocol to Clique or other:
- Add the `QUORUM_CONSENSUS` and optional `QUORUM_GETH_ARGS` environment variables:
  ```
  QUORUM_CONSENSUS=clique \
  QUORUM_GETH_ARGS=" --mine --minerthreads 1--syncmode full" \
  docker-compose up -d
  ```

- Debug logs - check for things like blocks are being mined from your `--mine` flag, 
  or for out-of-memory errors, or a node is waiting on tessera node to startup.
  - docker-compose log utility:  
    `docker-compose logs --tail 100 -f node1`
  - Ubuntu:
    1. Check containers directory:  
        - apt installed docker:  
          `CONTAINER_PATH=/var/lib/docker/containers`
        - snap installed docker:  
          `CONTAINER_PATH=/var/snap/docker/common/var-lib-docker/containers`
    1. `ls -l $CONTAINER_PATH`
    1. `tail -f $CONTAINER_PATH/<container hash>/<container hash>-json.log`
  - Mac: (Newer versions of Docker)
    1. Enter the vm in console tab:  
      `screen ~/Library/Containers/com.docker.docker/Data/vms/0/tty`
    1. Within the screen session:  
      `ls -l /var/lib/docker/containers`
    1. `tail -f /var/lib/docker/containers/<container hash>/<container hash>-json.log`
