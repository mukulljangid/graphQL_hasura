# GraphQL

### :pushpin: Step 1
**TITLE:**    
GraphQL

**TOPIC:**    
GraphQL using Hasura

**DESCRIPTION:**    
GraphQL is a language for quering API's. It is fast and efficient beacuse it provides you the flexibility and ask for the results in the way or format that you want. It requires both server side (with some exposed endpoints) and client side components to build the bridge as a language for communication. 

### :pushpin: Step 2
:family: **TARGET AUDIENCE:**    
Developers, organisations, applications and any user who would like to view some data that they want. 

### :pushpin: Step 3

**Beginning:**    
GraphQL is a specification for a query language. It just says how it should look and work. The actual implementations are Realy and Apollo. So to use GraphQL, we have to use an implementation of it. Import some libraries an you are all set to go.

**Middle:**    
GraphQL is a little different from a REST API. It just has one endpoint, which is /graphql POST request. So, after having these two parts fixed, the third would be ask for a what you want and this is the place where you write a GraphQL query and ask for what you want. A basic GraphQL query might look something like this:
{
query{
        movies{
                title
                director
                }
        }
}
It would return the name and genre of all the movies that would exist in a database.

**End:**    
GraphQL can be used with any server side language and any frontend framework. It is a really cool thing. We will further take a look at how Hasura would help us acheive this easily. Let's give it a shot.
