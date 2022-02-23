# Docker-craft
Simple Docker Compose config for Craft CMS  
Nginx, Mariadb, Webpack

# Setup
Place Craft CMS to /src
Place db_dump.sql into /db
Add {sitename}.loc to hosts file  
`{sitename}.loc`

# Create .env file
Copy .env.example to .env  
Edit .env file  

`BASE_URL=http://{sitename}.loc`  
`DB_DATABASE=db`  
`DB_USER=db_user`  
`DB_PASSWORD=secret`  

# Run docker
`docker-compose up`

# Import DB

Find mariadb docker container

`docker ps`

Login into mariadb container

`docker exec -it {mariadb_id} /bin/bash`

Import DB

`mysql -u db_user -p db < db_dump.sql`  
password: secret
