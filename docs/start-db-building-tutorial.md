# Building START-DB from Source

## Prerequisites

Ensure the following software is installed before building START-DB:

1. **Docker Desktop**  
   Download and install Docker Desktop from the [official website](https://www.docker.com/products/docker-desktop).  
   If prompted, enable Windows Subsystem for Linux (WSL).

   For detailed instructions on enabling WSL, refer to the [Windows Subsystem for Linux Documentation](https://learn.microsoft.com/en-US/windows/wsl/).

2. **IntelliJ IDEA**  
   Download and install the latest version of IntelliJ IDEA from the [official website](https://www.jetbrains.com/idea/).

3. **Oracle JDK 1.8 (Java 8)**  
   Download Oracle JDK 1.8 from the [official website](https://www.oracle.com/java/technologies/downloads/).  
   On Windows, the installation process is straightforward—follow the installation prompts.  
   If the JDK installer does not automatically add Java to your PATH, you will need to configure it manually.

   Verify the installation by running the following command in the Command Prompt:

   ```shell
   java -version
   ```

   Example output:

   ```text
   java version "1.8.0_351"
   Java(TM) SE Runtime Environment (build 1.8.0_351-b10)
   Java HotSpot(TM) 64-Bit Server VM (build 25.351-b10, mixed mode)
   ```

   If the version does not display, manually add the JDK to your PATH in the "Environment Variables" settings.

---

## Steps to Build

1. **Clone the Repository**  
   Clone the START-DB repository to your local machine:

   ```shell
   git clone git@github.com:Spatio-Temporal-Lab/start-db.git
   ```

2. **Set Up the Project in IntelliJ IDEA**  
   Open the cloned repository in IntelliJ IDEA as a project. Ensure that the project uses Java 1.8 and Scala 2.12.8.

3. **Run Docker Services**  
   Open the terminal in IntelliJ IDEA and navigate to the `docker/new-all` directory. Start the required services with the following command:

   ```shell
   docker-compose up -d mysql-local geomesa-hbase-local
   ```

4. **Update the Hosts File**  
   Add the following entries to your system’s `hosts` file:

   ```text
   127.0.0.1 mysql-local
   127.0.0.1 geomesa-hbase-local
   ```

5. **Build the Project**  
   In IntelliJ IDEA, go to `Maven > start-db > Lifecycle > package (Skip Tests)` to begin packaging the project. Ensure that Maven uses the central repository during this process.

---

## Starting the START-DB Server

**Ensure that the build process is complete before proceeding.**

1. **Load Docker Images**  
   Copy the `cluster-apache-spark.img` and `livy.img` files to the new-all directory, and load them into Docker:

   ```bash
   docker load -i cluster-apache-spark.img
   docker load -i livy.img
   ```

   Alternatively, pull and tag the necessary images:

   ```text
   docker tag <cluster-apache-spark_imgID> cluster-apache-spark:latest
   docker tag <livy_imgID> livy:latest
   ```

2. **Move JAR Files**  
   Copy the following JAR files into the new-all/start-db directory:

   - `start-db.jar`
   - `start-db-flink-1.0.0-SNAPSHOT-jar-with-dependencies.jar`

3. **Update Kafka Configuration**  
   Replace `your_ip`(such as `localhost`) in the Kafka configuration of the `docker-compose.yml` file with the IP address of your server.

4. **Update the Hosts File**  
   Add the following entries to your hosts file:

   ```text
   127.0.0.1 livy-local
   127.0.0.1 hadoop-local
   127.0.0.1 kafka
   127.0.0.1 jobmanager
   ```

5. **Start Docker Containers**  
   Use the following command to start the Docker containers:

   ```bash
   docker-compose --profile cluster up -d
   ```

6. **Start Backend and Frontend Services**  
   Refer to the START-DB [backend](https://github.com/Spatio-Temporal-Lab/start-db-backend) and [frontend](https://github.com/Spatio-Temporal-Lab/start-db-frontend) tutorials to initialize the respective services.

---

## Common Build Issues and Troubleshooting

1. **Maven Plugin Build Error**

   Ensure you are using the central Maven repository rather than a mirror. Clear the `.m2/settings.xml` file and rebuild the project:

   ```bash
   mvn clean package
   ```

2. **Test Failures**

   Skip tests during the build process by running:

   ```bash
   mvn clean package -DskipTests
   ```

3. **Out of Memory Errors**

   Increase the memory allocation for Maven during the build or consider reinstalling JDK if necessary.

4. **Missing Docker Images**

   If a required Docker image is missing (e.g., amazoncorretto:8-al2-generic-jdk), download it using:

   ```bash
   docker pull amazoncorretto:8-al2-generic-jdk
   ```

5. **JDK and JRE Version Mismatch**

   Ensure both JDK and JRE versions are set to 8 (1.8).

6. **Failed to Pull START-DB Image**

   If pulling the START-DB `image` fails, comment out the `image` line and uncomment the `build` section in the `docker-compose.yml` file:

   ```yaml
   start-db:
     # image: start-db-image:latest
     build:
       context: ./start-db
       dockerfile: ../start-db/Dockerfile
     ports:
       - "8000:8000"
     depends_on:
       - mysql-local
       - geomesa-hbase-local
       - livy
   ```
