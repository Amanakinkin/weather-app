# weather-app
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Weather app</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="preference">
    <input type="checkbox" name="weather app" id="weather app">
  </div>
  <div class="card">
    <div class="search">
      <input type="text" placeholder="enter city name" spellcheck="false"> <button><img src="serch.png" alt="serch"></button>
    </div>
    <div class="Weather">
      <img src="sun.png" class="weather-icon" alt="sun">
      <h1 class="temp">22℃</h1>
      <h2 class="city">New York</h2>
      <div class="details">
        <div class="col">
          <img src="waves.png" alt="waves">
          <div>
            <p class="humidity">50%</p>
            <p>Humidity</p>
          </div>
        </div>
        <div class="col">
          <img src="wind.png" alt="wind">
          <div>
            <p class="wind">15 km/hr</p>
            <p>Wind Speed</p>
          </div>
        </div>
      </div>
    </div>
  </div>
  <script>

        const apiKey = "abeeb3c849ebce57ff9428afb8d4817a"
        const apiUrl = "https://api.openweathermap.org/data/2.5/weather?=units=metric&q=";

        const searchBtn = document.querySelector('.search button')
        const searchBox = document.querySelector('.search input')


        async function checkWeather(city) {
            const response = await fetch (apiUrl+city+'&appid=${api Key}');
            var data = await response.json();

            console.log(data);

            document.querySelector(".city").innerHTML = data.name;
            document.querySelector(".temp").innerHTML = Math.round( data.main.temp) ;
            document.querySelector(".humidity").innerHTML = data.main.humidity + "%";
            document.querySelector(".wind").innerHTML = data.wind.speed + "km/h";
        }

        searchBtn.addEventListener("click", () =>{
            checkWeather(searchBox.value);
        })

  </script>
</body>
</html>
