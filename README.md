Build A REST API With Node.js, Express, & MongoDB - Quick 

Youtube: Web Dev Simplified video

https://www.youtube.com/watch?v=fgTGADljAeg

REST API NOTES/COMMANDS 

//npm init (so we can use node.js, express, and mongodb) 
//install dependencies 
    //npm i express mongoose 
    //mongoose allows us to interact with mongodb 
    //express is useful when we want to create an application using node.js
//install development dependencies
    //npm i --save-dev dotenv 
    //--save-dev makes it so these dev dependencies don't get installed in production
    //dotenv allows us to pull environment variables from a dotenv file
    //nodemon allows us to refresh the server when we make changes asynchronously
//package.json file we change "test" to "devStart" 
//create .env file and .gitignore file
    //add .env file to .gitignore because of sensitive information 
    //add node_modules folder to .gitignore 
//code server.js 
    //require express library
    //create app variable to configure the server using express() 
    //app.listen assigned to port 
//configure mongoose to connect to mongodb 
    //require mongoose 
    //mongoose.connect
//create variable db to hook up events that will run when our app is connected
    //db.on is to catch errors if there's a problem connecting
    //db.once runs once, saying we opened and connected to database
//set our mongodb database string to an environment variable in .env
    //configure dotenv to use dotenv library to use environment variables saved in .env
//set up server to accept JSON
    //app.use will allow us to use any middleware that we want
    //middleware is code that runs when the server gets a request, but before it gets passed to our routes
//create our routes
    //create routes folder
    //create file subscribers.js
    //create subscribers router in server.js
    //app.use in server.js to pass the path we want '/subscribers'
//set up subscribers route
    //require express
    //use router portion from express
//set up our routes 
    //configure the routes
        //.get to get all subscribers or just one
        //.post to create new subscriber
        //.patch to update what the user passes us
        //.delete to delete subscriber
    //set up the route '/' to the current folder 
    //each route take a request and response function
//create models folder
    //create subscriber.js model file 
    //require mongoose 
        //mongoose allows us to create a model which we use to interact with mongodb
    //create schema and set it to new mongoose.Schema
    //mongoose.Schema will take in a JavaScript object which will have keys for all the different properties of our subscriber object
    //export schema
        //mongoose.model function takes two properties 
            //first is the name of the model 'Subscriber'
            //second is the schema that corresponds (subscriberSchema)
            //when we export and import it into a different file, this model allows us to interact directly with the database using this schema
//import subscriber.js in models to subscribers.js in routes 
//GET
    //Get all route using async await 
    //const subscribers will be set to our Subscriber model .find() too get all subscribers
    //wrapped in a try catch block
//POST 
    //Create subscriber route using async await 
    //const subscriber will be = new Subscriber which will take a Javascript object
    //save the new created user using a try catch block
    //it will await subscriber.save() if it is successfull it will be saved to const newSubscriber
    //the response status will be 201 or "successfully created an object"
    //the catch error status will be 400 - when the user gives bad data. It ain't our fault!
//UPDATE ONE, PATCH AND DELETE 
    //all take an :id that we pass to it in the beginning to get the subscriber
//create middleware function that we can use for all three routes 
    //async getSubscriber 
    //it has (req, res, next) as the properties
    //next means to move onto the next section of our code, which will be the callback (req, res) {} of the original route 
    //we will be able to call res.subscriber in all of the routes that we set in our function
    //we use return in this function in order to stop the function from going any further if a user is not passed 
    //next() at the end of the function to move onto the next middleware, or the actual request itself in the route