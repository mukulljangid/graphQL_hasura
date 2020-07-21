# GraphQL Technical Blog (Hasura)
GraphQL is changing the way modern apps are built!
Making API requests using Hasura and quickly fetching responses using GraphQL.
Hasura gives you the goodness of GraphQL without the pain of having to set it up.
Hasura is a fully GraphQL spec compliant server and connects to databases & services to provide a secure and scalable unified GraphQL API.

## Steps to setup the environment and include library in our code

For setting up an API on Hasura, we might need a prerequisite of setting up a postgres database to further include a link to it when we create a project.
Hasura doesn't have an option of importing a database from local, it needs to be hosted somewhere, let's say, in an AWS S3 bucket.
Also, if you are looking to set up Hasura on local using the docker compose file, you might want to set up Docker and Docker compose first. More information about that can be found here: https://hasura.io/docs/1.0/graphql/manual/getting-started/docker-simple.html

### Step 1: Logging in to Hasura
If you are looking to do on local, have the GraphQL engine ready using docker-compose and the Hasura console to get started. Another option is to use the online console. Online console would be really convenient for a quickstart.

### Step 2: Setting up Database
You can sign in to Hasura and then if you have an existing postgres database, enter the connection URI. You can also setup a free heroku database for which you setup a Heroku account and create tables and insert rows manually one at a time. 

### Step 3: Calling API using Hasura console
Let us consider a movies table with the following columns: { title - text, release_year - integer, production_compamy - text, director - text, writer - text, actor1 - text, actor2 - text, id - integer } 
where, id - primary key, unique

- As soon as we create a table on our console, if we look at the explorer, we have different options to just do a couple of clicks and it will create a query for us. *No typing needed*.

<img width="222" alt="Screenshot 2020-06-23 at 11 55 07 PM" src="https://user-images.githubusercontent.com/49061120/85498127-1dabf600-b5ad-11ea-9292-64932ccc4416.png"><img width="216" alt="Screenshot 2020-06-23 at 11 55 35 PM" src="https://user-images.githubusercontent.com/49061120/85498160-2997b800-b5ad-11ea-82d6-d3a5beea9c9e.png"><img style="float: right;" width="225" alt="Screenshot 2020-06-23 at 11 41 12 PM" src="https://user-images.githubusercontent.com/49061120/85497737-716a0f80-b5ac-11ea-8572-6f820ed5db04.png">

In the explorer you might see two extra tables which are being created for us. One of them is for aggregated quering. Here, the aggreagate function we are using is max and the column to get the max from is release_date which produces our output.
<img width="818" alt="Screenshot 2020-06-24 at 12 07 39 AM" src="https://user-images.githubusercontent.com/49061120/85498982-bdb64f00-b5ae-11ea-919d-49b9c1d204b2.png">

And other is for parameterised primary key quering, where you check the starred primary key and pass a value as the parameter and it will fetch a unique tuple for you with that value of primary key.
<img width="819" alt="Screenshot 2020-06-24 at 12 05 17 AM" src="https://user-images.githubusercontent.com/49061120/85498987-c018a900-b5ae-11ea-9546-2d3c17c2c6bf.png">


- As soon as we click on a dropdown, the table name gets added to the query and by checking the column boxes we can the columns being to be retrieved and being added in the order they are checked.
<img width="1018" alt="Screenshot 2020-06-24 at 12 22 53 AM" src="https://user-images.githubusercontent.com/49061120/85500115-e0e1fe00-b5b0-11ea-8bd5-1c0b98c7436e.png">

- Working with conditional querying. Various conditions like and, or, not and conditions on columns can be added, for eg, below we are trying to find rows where production_company name equals "Liberty Film".
<img width="1187" alt="Screenshot 2020-06-24 at 12 26 10 AM" src="https://user-images.githubusercontent.com/49061120/85500336-5352de00-b5b1-11ea-90b6-fb2f824d1984.png">

- Another approach to do the same thing is by adding and condition first and including as many column conditions as you like which gives it more flexibilty.
<img width="1160" alt="Screenshot 2020-06-24 at 12 37 53 AM" src="https://user-images.githubusercontent.com/49061120/85501247-f7895480-b5b2-11ea-96db-ee7731018500.png">

#### Scope
- Just for testing purposes, you can try making an API call from Postman by entering headers from the hasura console and entering your query in the body of the request. Looks something like this:
<img width="1127" alt="Screenshot 2020-06-24 at 8 19 57 AM" src="https://user-images.githubusercontent.com/49061120/85555490-faf10000-b5f3-11ea-9bcc-4c20fef13a6e.png">
And you know, if it worked on postman, it will respond to any code request that comes in.

- Remote schema, a GraphQL external service, can be used to connect to Hasura, by just pointing to the Hasura API endpoint from the GraphQL service. 

- Hasura can be used to create event triggers on tables. An Event Trigger atomically captures events (insert, update, delete) on a specified table and then reliably calls a webhook that can carry out any custom logic.

More information can be found on https://hasura.io/opensource/

### Summary
For condensing the entire process into a couple of lines, all we need is a hasura account and a database which can be linked to hasura and we can then get straight to API making. Start checking boxes of the columns we want to display in your query. Select them in the order that we would like it to be displayed. See that the query formed is correct and has no red lines to indicates errors and then we can shoot it to see the results! Use aggregate functions and form more complex queries and still expect the result to be really quick. That's the benefit of Hasura and we can use it to back any application we like.

### Conclusion

- No developer would have ever thought that hitting an API and forming a request (as a query) by just clicking around would be so easy. Thank you for following along.
