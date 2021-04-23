/* Global Variables */
const baseURL = "http://api.openweathermap.org/data/2.5/weather?zip=";
const apiKey = "&appid=9f95a83661de976d8ba0a3a3ce3124f3";

// Create a new date instance dynamically with JS
let d = new Date();
let newDate = d.getMonth()+'.'+ d.getDate()+'.'+ d.getFullYear();

const button = document.querySelector("#generate");

button.addEventListener("click", (e) => {
    const zipCode = document.querySelector("#zip").value;
    getWeatherData(baseURL, zipCode, apiKey)
});

const getWeatherData = async (baseURL, zipCode, apiKey) => {
    const res = await fetch(baseURL + zipCode + apiKey)
    const data = await res.json()
    .then((data) => { 
        const userResponse = document.querySelector("#feelings").value;
        const dataObject = {
            temperature: data.main.temp,
            date: newDate,
            userResponse: userResponse,

        }
        postData("/addWeatherData", dataObject)
    })
    .then(
        updateUI()
    )
}

// Async POST
const postData = async ( url = '', data = {})=>{

    const response = await fetch(url, {
    method: 'POST', 
    credentials: 'same-origin', 
    headers: {
        'Content-Type': 'application/json',
    },
    body: JSON.stringify(data), // body data type must match "Content-Type" header        
  });

    try {
      const newData = await response.json();
      return newData;
    }catch(error) {
    console.log("error", error);
    }
};

const updateUI = async () => {
    const res = await fetch('/all')
    const allData = await res.json();
    try{
      document.querySelector('#date').innerHTML = `Date: ${allData.date}`;
      document.querySelector('#temp').innerHTML = `Temperature: ${allData.temperature}°F`;
      document.querySelector('#content').innerHTML = `You are feeling ${allData.userResponse}`;
  
    }catch(error){
      console.log("error", error);
    }
  }