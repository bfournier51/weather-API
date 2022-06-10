# weather-API
Determine the weather and temperature in any city with the use of an API

import requests

API_KEY = "3da806821d1cd3ec1f7d3f0c0e4ce3aa"

BASE_URL = "http://api.openweather.org/data/2.5/weather"

city = input("Enter a city name: ")
request_url = f"{BASE_URL}?appid = {API_KEY}&q = {city}"
response = requests.get(request_url)

if response.status_code == 200:
    data = response.json()
    weather = data['weather'][0]['description']
    print("The weather is:",weather)
    temperature = round(data["main"]["temp"] - 273.15,2)
    print("The temperature is:", temperature, "Celcius")


else:
    print("An error ocurred.")
