import requests
import matplotlib.pyplot as plt
from datetime import datetime

API_KEY = '7ea0b84a40f9f8050168e9f1dcb5c5c8'  
CITY = 'Mumbai'
UNITS = 'metric'  # For temperature in Celsius
URL = f'https://api.openweathermap.org/data/2.5/forecast?q={CITY}&appid={API_KEY}&units={UNITS}'

try:
    response = requests.get(URL)
    data = response.json()

    if 'list' not in data:
        print("API Error:", data)
        exit()

except Exception as e:
    print("Error fetching data:", e)
    exit()

timestamps = []
temperatures = []
humidities = []

for entry in data['list']:
    dt = datetime.fromtimestamp(entry['dt'])
    temp = entry['main']['temp']
    humidity = entry['main']['humidity']

    timestamps.append(dt)
    temperatures.append(temp)
    humidities.append(humidity)

plt.figure(figsize=(14, 8))

# Temperature subplot
plt.subplot(2, 1, 1)
plt.plot(timestamps, temperatures, marker='o', color='red', label='Temperature (°C)')
plt.title(f"5-Day Weather Forecast for {CITY}")
plt.ylabel("Temperature (°C)")
plt.grid(True)
plt.xticks(rotation=45)
plt.legend()

# Humidity subplot
plt.subplot(2, 1, 2)
plt.plot(timestamps, humidities, marker='x', color='blue', label='Humidity (%)')
plt.xlabel("Date & Time")
plt.ylabel("Humidity (%)")
plt.grid(True)
plt.xticks(rotation=45)
plt.legend()

plt.tight_layout()
plt.savefig("mumbai_weather_forecast.png")
plt.show()
