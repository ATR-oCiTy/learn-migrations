
### Setup and tips  
  
- Ensure **lima** is installed and the following alias is added: ```alias docker=lima nerdctl```  
  
- Create the **cart** database and run the database server in a docker container: ```docker run --name postgrescartdb -e POSTGRES_DB=cart -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres -p 5432:5432 -d postgres```  
  
- Open interactive shell in the newly created running container: ```docker exec -it  postgrescartdb /bin/bash```  
  
- Login to postgres db shell: ```psql -U postgres -d cart```  
  
- To list tables: ```\dt```  
  
- To show table schema: ```\d+ <tablename>``` 

- Add migrations in *"src/main/resources/db/migration"* with correct naming convention: ```V<version>__<Migration Name>.sql```
  
- To list all gradle tasks: ```./gradlew tasks```  
  
- To migrate database: ```./gradlew flywayMigrate```  
  
### Required migrations  
  
* **Create tables**
    * users(id, name, address)
    * products(id, name, price)

* **Alter tables**
	* Alter ‘name’ field to ‘full_name’ in users table
	* Adding primary phone number to the users table

* **Create tables**
	* carts(id, user_id)
	* cart_items(id, cart_id, product_id, quantity)

*Refer: https://flywaydb.org/documentation/*
