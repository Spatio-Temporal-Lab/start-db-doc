# START-DB Localhost Tutorial

The localhost tutorial especial for the developer.

ATTENTION: before reading this file, make sure that you have read the `start-db-package-tutorial` and successfully done the package operation.

## Run Docker
The container in docker named `new-all` should keep running during any other oerations.

## Prepare necessary repositories on your local disk

You should clone the `start-db-fronted`, `start-db-backend` and `start-db` from the GitHub.

Following the instruction of `start-db-package-tutorial`, you will find a folder named `target` in the source path of `start-db`. This is the final output of the package operation. Open the `target` folder you will find `start-db.jar`, the executable engine package.

Do the similar thing in `start-db-backend` repository. Also in the `target` folder, you will find `original-start-db-backend-0.0.1-SNAPSHOT.jar`, the executable backend package. Pay attention to the `original` prefix.

> An easy way to determine whether your package is working correctly is to wait for a few seconds and see if there is an error.

The operation in the `start-db-fronted` is much easier. Just follow the README and run the code step by step:

```shell
# install necessary package
npm install

# Compile and Hot-Reload for Development
npm run dev

# The third command is not necessary for developing project.
```

## Download Redis
To run the server locally, the [Redis](https://github.com/tporadowski/redis/releases) is integral.Download the zip file and decompress it in any folder you like.

Then run the cmd in the folder that contains the decompressed files of Redis:

```shell
redis-server.exe redis.windows.conf
```

If it correctlly works, don't kill the window and minimize it.

## Run server

Right click the mentioned packages in each reporitory and run them follow the order: `start-db` -> `start-db-backend` -> `start-db-fronted`

## Log in
Send the correct user name and password, you will successfully run the service locally.