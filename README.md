# NOTES-CRUD

Overview of Today. 

We're going to finish our CRUD app by adding the ability to update the information of our card. 

(Talk through what we did yesterday. Walk through the form logic again ect.)

## Server side. 

Lets add another endpoint 
```javascript
app.put('/movies/:id', async (req,res) => {
	const updateMovie = await Movie.findByIdandUpdate(req.params.id, req.body)
	res.status(200).json(updateMovie)
})
```

First, lets try to understand this part `app.put('/movies/:id', async (req, res) => {...})` method is an Express route handler for handling HTTP PUT requests made to the '/movies/:id' path. 
The `:id` is a route parameter, a placeholder for the actual ID of the movie we want to update. 

When a put request is made to this endpoint, the anonymous async function provided as the second argument is invoked. This function takes two arguments 'req' (short for request) and 'res' (short for response). The names req/request and res/response are arbitrary. We could name them anything we want -> But they will always represent the request and response objects. 

The 'req' object is an instance of 'http.IncomingMessage` (don't worry about this too much lol) and it has many useful properties and methods. 

==Some properties we've been using are req.params , req.body and req.query.== 

^ Update this with more detail .

- req.body contains the parsed JSON body of the request (using body-parser)
- req.params contains route parameters - EG 
  ```
  
  
  ```

	

## Front End 

Let's start by refactoring our code a little. I'm going to move some of the logic we wrote earlier back into our Form component. 

-> Let's create a new function called handleUpdateMovie.js

```javascript
const handleUpdateMovie.js = async (movie) => {
	await axios.put(`http://localhost4242/movies/${movie._id}`, movie)
	getMovies();
}
```

- like with our delete, we're using the movies ID to send the put request to the correct endpoint
- We're also passing the movie object -> this had the data of the card we've clicked on. Our server will use this later.  

