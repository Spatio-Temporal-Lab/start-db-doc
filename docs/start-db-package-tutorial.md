# START-DB Package Tutorial

## For Linux users

**Linux distribution: Ubuntu 22.04 LTS**

Operations may differ on different distributions.

1. Install **maven**

   `sudo apt install maven`

   > If you are the root user, `sudo` is not necessary:
   >
   > `apt install maven`

   _Get the system updated before you install a new package to avoid other problems:_

   `sudo apt update && sudo apt upgrade`

   > Like what we mentioned above, `sudo` is not necessary for the root user:
   >
   > `apt update && apt upgrade`

2. Install **OpenJDK**

   `sudo apt install openjdk-11-jdk`

   And run this command to check if **OpenJDK** is installed and configured properly:

   `java --version`

   The output message should be like:

   ```
   openjdk 11.0.17 2022-10-18
   OpenJDK Runtime Environment (build 11.0.17+8-post-Ubuntu-1ubuntu222.04)
   OpenJDK 64-Bit Server VM (build 11.0.17+8-post-Ubuntu-1ubuntu222.04, mixed mode, sharing)
   ```

3. Install **docker.io** & **docker-compose**

   `sudo apt install docker.io && sudo apt install docker-compose`

   Then run a command for test:

   `sudo docker run hello-world`

   If Docker Engine is installed, the output message should be like:

   ```
   ......
   Hello from Docker!
   This message shows that your installation appears to be working correctly.

   ......
   ```

4. If you do not have a local copy of **START-DB** 's source code, clone it or download the zip file of it.

5. Now change the working directory into start-db.

6. Run the following command to run containers as dependency.

   `sudo docker-compose -f docker/local/docker-compose.yml up -d`

7. Set MySQL host

   `echo "127.0.0.1 mysql-local" | sudo tee -a /etc/hosts`

8. Set GeoMesa HBase host

   `echo "127.0.0.1 geomesa-hbase-local" | sudo tee -a /etc/hosts`

9. Compile and package

   `mvn package`

## For Windows/Mac OS Users

1. Download and install **Docker Desktop**

> Here is the official link: [Docker Desktop](https://www.docker.com/products/docker-desktop/)

2. Install the latest version of **IntelliJ IDEA**

3. If you do not have a local copy of **START-DB** 's source code, clone it or download the zip file of it.

4. Open **START-DB** as a project using **IntelliJ IDEA**.

   _Please click "Trust Project" if there is a safety-notice dialog._

5. Open the terminal in **IntelliJ IDEA** and run the following command:

   `docker-compose -f docker/local/docker-compose.yml up -d`

6. Add two lines in your hosts file:

   ```
   127.0.0.1 mysql-local
   127.0.0.1 geomesa-hbase-local
   ```

7. Click "Maven > start-db > Lifecycle > package"in **IntelliJ IDEA** and packaging will begin.

## TIPS

1. It is recommended to drop all containers and restart them before every test.
2. If there is any network problem during synchronization of maven repositories or docker images, please delete the cache and retry.
3. Administrator privilege is needed for editing the hosts file.
