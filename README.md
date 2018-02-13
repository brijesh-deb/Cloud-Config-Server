## Cloud Config Server Sample
### Problem Statement
How to externalize configuration properties, have environment (dev,qa, prod) specific configurations and update properties at runtime without service redeployment.
### Solution
Use a config server like Spring Cloud Config Server with Git integration
### Code rundown
- Add Config Server annotation in Spring Application class: ***@EnableConfigServer***
- Create a local folder "config-server-repo". 
- Place 3 properties files in this folder: client-server-client.properties, client-server-client-dev.properties, client-server-client-prod.properties
- Run command ***git init*** in config-server-repo directory to make it a git repository. Later it can be converted to a remote repository by configuring its URL in propertie s file.
- Run ***git add .*** to all files in the repository.
- Commit the files by running command ***git commit -m "Initial commit"***
- bootstrap.properties in resources folder has config server settings

### Run and test
- mvn clean install
- Run the application
- Test configurations for different environments with following end-points
  - http://localhost:8888/config-server-client/dev
  - http://localhost:8888/config-server-client/prod
- Test runtime changes in configurations
  - Change config-server-client-dev.properties and config-server-client-prod.properties files
  - Commit the files in git repo
  - Now again run hit the end-points, changes will get reflected (without server restart)


