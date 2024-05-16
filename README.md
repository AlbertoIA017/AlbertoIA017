import streamlit as st
import requests

def fetch_weather_forecast(city_name):
    api_key = "tu_clave_api_aqui"  # Reemplaza esto con tu clave API
    base_url = "http://api.openweathermap.org/data/2.5/weather?"
    complete_url = f"{base_url}q={city_name}&appid={api_key}&units=metric"
    response = requests.get(complete_url)
    data = response.json()
    return data

def main():
    st.title("Aplicación de Pronóstico del Tiempo")

    city_name = st.text_input("Ingrese el nombre de la ciudad:", "Ciudad")
    if st.button("Obtener Pronóstico"):
        weather_data = fetch_weather_forecast(city_name)
        if weather_data["cod"] != "404":
            main_weather = weather_data["main"]
            weather_description = weather_data["weather"][0]["description"]
            st.write(f"Temperatura: {main_weather['temp']}°C")
            st.write(f"Sensación Térmica: {main_weather['feels_like']}°C")
            st.write(f"Humedad: {main_weather['humidity']}%")
            st.write(f"Descripción: {weather_description}")
        else:
            st.write("Ciudad no encontrada. Por favor, ingrese otro nombre.")

if __name__ == "__main__":
    main()
  
<!---
AlbertoIA017/AlbertoIA017 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
