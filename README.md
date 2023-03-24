# Genetta-Server
Genetta requires a neo4j server active and running with the APOC, and GDS plugins enabled. 
Genetta contains a docker-compose file which can be used to fully setup and start the web application.

## Installation
### Docker
1. Download and install docker `https://docs.docker.com/get-docker/`
1. Navigate to this directory.
3. `sudo chmod +x startup.sh`
4. `./startup`

### Without Docker
If docker is not available, here is a brief guide to installing neo4j with links to more comprehensive installation guides. 
Note this guide assumes a Debian based operating system.
*  Install Neo4j (https://neo4j.com/docs/operations-manual/current/installation/)
	1. `$ wget -O - https://debian.neo4j.com/neotechnology.gpg.key | sudo apt-key add -`
	2. `$ echo 'deb https://debian.neo4j.com stable latest' | sudo tee -a /etc/apt/sources.list.d/neo4j.list`
	3. `$ sudo apt-get update`
	4. `$ sudo apt-get install neo4j=1:4.4.6`
* Enable APOC (https://neo4j.com/labs/apoc/4.1/installation/)
	1. `$ mv NEO4J_HOME/labs/apoc-4.4.0.3-core.jar $NEO4J_HOME/plugins` (usually `mv /var/lib/neo4j/labs/apoc-4.4.0.3-core.jar /var/lib/neo4j/plugins`).
	2. `$ sudo neo4j restart`
* Install GDS (https://neo4j.com/docs/graph-data-science/current/installation/neo4j-server/)
	1. Download 'neo4j-graph-data-science-[version].jar' from the [Neo4j Download Center](https://neo4j.com/download-center/#algorithms)
	2. Copy it into the `$NEO4J_HOME/plugins` directory (usually `/var/lib/neo4j/plugins`).
	3. Add `dbms.security.procedures.unrestricted=gds.*` and `dbms.security.procedures.allowlist=gds.*` to `$NEO4J_HOME/conf/neo4j.conf` (usually `/var/lib/neo4j/conf/neo4j.conf`).
	4. `$ sudo neo4j restart`
