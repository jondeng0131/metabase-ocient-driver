# Metabase Ocient Driver

💥*Note:* This project is under active development

## Installation
There are a few options to installing a Metabase community driver. The simplest is to copy the JAR file into the plugins directory in your Metabase directory (the directory where you run the Metabase JAR). Additionally, you can change the location of the plugins directory by setting the environment variable `MB_PLUGINS_DIR`.

### Docker
Use the [`Dockerfile`](./Dockerfile) to build an image of Metabase with the Ocient driver pre-installed:
```shell
git clone git@github.com:Xeograph/metabase-ocient-driver.git
cd metabase-ocient-driver
git submodule update --init
make docker-build
```

### Use custom Metabase JAR
If you already have a Metabase binary release (see [Metabase distribution page](https://metabase.com/start/jar.html)):

1. Download the Ocient driver jar from this repository's ["Releases"](https://github.com/Xeograph/metabase-ocient-driver/releases) page.
2. Create a directory and copy the `metabase.jar` to it.
3. In that directory create a sub-directory called `plugins` and copy the Ocient driver jar into it.
4. From the directory created in step 2, run `java -jar metabase.jar`.

## Contributing

### Prerequisites

- java >= 8
- [Leiningen](https://leiningen.org/)
- [Install metabase-core](https://github.com/metabase/metabase/wiki/Writing-a-Driver:-Packaging-a-Driver-&-Metabase-Plugin-Basics#installing-metabase-core-locally)

### Connecting to Ocient
To add a database connection, click on the gear icon in the top right, and navigate to Admin settings > Databases > Add a database.
Enter the following fields in your connection settings: 
-Display Name	(Display name for database)
-Host	(The host name or IP address of the SQL node of your Ocient database.) 
-Port	(The port number for your connection. Unless you have altered this, the default Ocient port is 4050)
-Database name	(The name of the database you want to connect to)
-Schemas	(The identifier for any schemas you want to use)
-Authentication Method	(Choose between SSO and Password)
-Username	(The username for your database)
-Password	(The password associated with your username)
-Type of SSO token	(access_token)
-SSO token	(Your SSO access token string)

*Note: To use SSO authentication, you must SSO integration enabled for the specified database and group. For more information, see ALTER DATABASE SET SSO INTEGRATION. 



### Build from source

The Ocient driver, can be built using [`Clouure Tools`](https://clojure.org/releases/tools):

```shell
# Outputs jar to `plugins/ocient.metabase-driver.jar` 
make build
```

### Run a local Metabase instance
To run a local instance of Metabase, run:

```shell
make run
```

### Run unit tests
To run the unit tests against the Ocient driver, run:

```shell
make run-unit-test
```
