# Weather-Checker-in-Python

import requests

API_KEY = "your_openweathermap_api_key"
BASE_URL = "http://api.openweathermap.org/data/2.5/weather"

def get_weather(city):
    url = f"{BASE_URL}?q={city}&appid={API_KEY}&units=metric"
    response = requests.get(url)
    data = response.json()
    
    if data.get("cod") != 200:
        print("City not found!")
    else:
        main = data["main"]
        weather = data["weather"][0]
        print(f"City: {city}")
        print(f"Temperature: {main['temp']}°C")
        print(f"Weather: {weather['description'].capitalize()}")

city = input("Enter city name: ")
get_weather(city)
