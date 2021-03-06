## Objective
The objective of this lesson is get the lab's source code up and running, seed the application with data and then check to make sure that the data seeding was successful.

## Steps

**Step 1:** Confirm that you're in the lab's working directory

`cd ~/simplecqrs && pwd`{{execute T1}}

You'll get the following output:

`/root/simplecqrs`

**Step 2:** Install the application's dependencies

`npm install`{{execute T1}}

You'll get output similar to the following:

```
.
.
added 293 packages from 643 contributors and audited 294 packages in 13.9s

23 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

```

**Step 3:** Install the application's backing services which are a single relational database, [`MariaDB`](https://mariadb.org/), a document database, [`MongoDB`](https://www.mongodb.com/2) and the [`Apache Kafka`](https://kafka.apache.org/) message broker. All the backing services throughout the lessons will run as an aggregation of containers under [`docker-compose`](https://docs.docker.com/compose/).

`docker-compose -f docker-compose-debug.yml up -d`{{execute T1}}

Confirm that the containers are running:

`docker ps -a`{{execute T1}}

You'll get output similar to the following:

```
CONTAINER ID        IMAGE                         COMMAND                  CREATED              STATUS              PORTS                                        NAMES
db48e703510b        confluentinc/cp-kafka:5.3.0   "/etc/confluent/dock…"   About a minute ago   Up About a minute   0.0.0.0:9092->9092/tcp                       simplecqrs_kafka2_1
e1c27560c295        zookeeper:3.4.9               "/docker-entrypoint.…"   About a minute ago   Up About a minute   2888/tcp, 0.0.0.0:2181->2181/tcp, 3888/tcp   simplecqrs_zookeeper_1
b547d11c26d6        mariadb                       "docker-entrypoint.s…"   About a minute ago   Up About a minute   0.0.0.0:3306->3306/tcp                       simplecqrs_mariadb_1
e99cc6537575        mongo:latest                  "docker-entrypoint.s…"   About a minute ago   Up About a minute   0.0.0.0:27017->27017/tcp                     mongodb
455588dc4fdb        adminer                       "entrypoint.sh docke…"   About a minute ago   Up About a minute   0.0.0.0:8080->8080/tcp                       simplecqrs_adminer_1
ece24fb49365        registry:2                    "/entrypoint.sh /etc…"   2 minutes ago        Up 2minutes    

```

**Step 4:** Export the environment variable that declares the port on which the application is to run.

`export APP_PORT=9001`{{execute T1}}

**Step 5:** Export the environment variable that declares URL on which the read source is running. (We'll cover the reasoning behind using separate read and write datasources in the following lessons.)

`export MONGODB_URL=mongodb://localhost:27017/simplecqrs_r`{{execute T1}}

**Step 6:** Start the application

`npm start`{{execute T1}}

You'll get the following output:

```
connected
Read database connected at Wed Dec 30 2020 04:12:31 GMT+0000 (Coordinated Universal Time)
server is listening on 9001

```

**Step 7:** In a second terminal window, seed the application with data

`cd simplecqrs && npm run seed`{{execute T2}}

You'll get output similar to the following:

```
Seeded {"count":0,"customerEmail":"Katheryn.Batz@nels.info","customerFirstName":"Katheryn","customerLastName":"Batz","description":"eum sit atque earum"}  at Wed Dec 30 2020 01:47:41 GMT+0000 (Coordinated Universal Time)
Seeded {"count":8,"customerEmail":"Lavonne.Kemmer@adolph.com","customerFirstName":"Lavonne","customerLastName":"Kemmer","description":"veritatis voluptas sint repellat"}  at Wed Dec 30 2020 01:47:41 GMT+0000 (Coordinated Universal Time)
Seeded {"count":7,"customerEmail":"Christop.Kilback@myrna.org","customerFirstName":"Christop","customerLastName":"Kilback","description":"aut rerum quas hic"}  at Wed Dec 30 2020 01:47:41 GMT+0000 (Coordinated Universal Time)
Seeded {"count":8,"customerEmail":"Cielo.O'Hara@janet.info","customerFirstName":"Cielo","customerLastName":"O'Hara","description":"explicabo aut ut dicta"}  at Wed Dec 30 2020 01:47:41 GMT+0000 (Coordinated Universal Time)
Seeded {"count":7,"customerEmail":"Abbigail.Welch@murl.name","customerFirstName":"Abbigail","customerLastName":"Welch","description":"aliquid iste aspernatur natus"}  at Wed Dec 30 2020 01:47:41 GMT+0000 (Coordinated Universal Time)
Seeded {"count":10,"customerEmail":"Henriette.DuBuque@ezra.org","customerFirstName":"Henriette","customerLastName":"DuBuque","description":"voluptatem nihil unde ut"}  at Wed Dec 30 2020 01:47:41 GMT+0000 (Coordinated Universal Time)
Seeded {"count":2,"customerEmail":"Vivianne.Dibbert@westley.org","customerFirstName":"Vivianne","customerLastName":"Dibbert","description":"nemo est id molestiae"}  at Wed Dec 30 2020 01:47:41 GMT+0000 (Coordinated Universal Time)
Seeded {"count":9,"customerEmail":"Hallie.Thiel@collin.info","customerFirstName":"Hallie","customerLastName":"Thiel","description":"cupiditate saepe dolores reprehenderit"}  at Wed Dec 30 2020 01:47:41 GMT+0000 (Coordinated Universal Time)
Seeded {"count":7,"customerEmail":"Stephanie.Jones@martine.net","customerFirstName":"Stephanie","customerLastName":"Jones","description":"dolorum beatae repellendus nesciunt"}  at Wed Dec 30 2020 01:47:41 GMT+0000 (Coordinated Universal Time)
Seeded {"count":2,"customerEmail":"Sarah.Hyatt@joannie.net","customerFirstName":"Sarah","customerLastName":"Hyatt","description":"inventore consequatur qui aut"}  at Wed Dec 30 2020 01:47:41 GMT+0000 (Coordinated Universal Time)
```

**Step 8:** Click the following link to verify that the data seeding has been successful.

https://[[HOST_SUBDOMAIN]]-9001-[[KATACODA_HOST]].environments.katacoda.com/orders


You'll get output similar to the following:

![orders output](msdb-004/assets/orders.png)

---

***Next: Analyzing the Application***