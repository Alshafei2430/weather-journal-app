// Setup empty JS object to act as endpoint for all routes
projectData = {};

// Require Express to run server and routes
const express = require('express');

//specifying port 3000 for the server to listen for
const port = 3000;

// Start up an instance of app
const app = express()

/* Middleware*/
//Here we are configuring express to use body-parser as middle-ware.
const bodyParser = require("body-parser")

app.use(bodyParser.urlencoded({ extended: false }));
app.use(bodyParser.json());

// Cors for cross origin allowance
const cors = require('cors')

app.use(cors())

// Initialize the main project folder
app.use(express.static('website'));


// Setup Server
const server = app.listen(port, () => {
    console.log(`listening on port ${port}`)
})

app.get('/all', (req, res) => {
    res.send(projectData)
})


app.post("/addWeatherData", (req, res) => {
    projectData = {
        temperature: req.body.temperature,
        date: req.body.date,
        userResponse: req.body.userResponse,
    }
    res.send(projectData)
})