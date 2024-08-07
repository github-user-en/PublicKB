# Weather Datasets
## US Weather Data
- {Google Search Query:} 
	- national weather service hourly weather data
- {Historical Data:} https://www.ncei.noaa.gov/cdo-web/datatools
- {Forecast Data:} https://www.weather.gov/documentation/services-web-api
	- {Weather Forecast Office Details using WFO ID:} https://www.weather.gov/<wfo_id>/

## India Weather Data
- {Historical Data:}
- {Forecast Data:} https://city.imd.gov.in/citywx/localwx.php

# Ground Transport Datasets
## Taxi Demand
### NYC Taxi Demand
- {Historical Data:} https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page
- {Forecast Data:} https://api.weather.gov/gridpoints/{OKX}/{latitude},{longitude}
	- New York Central Park example: https://api.weather.gov/gridpoints/OKX/40,73
	- Known Issues:
		- There is a bug that causes outages of forecast from the API when forecasts cross into a different year. This will be fixed before the end of 2024.
		- The gridpoints endpoint returns a 500 error. Retrying the request generally returns valid data.
		- `/forecast` and `/forecast/hourly` will return `temperature` and `dewpoint` in different units (Fahrenheit and Celcius). To make them be returned in same unit, use the `Feature-Flags: forecast_temperature_qv,forecast_wind_speed_qv` header in your request. [Reference: Forecast issues](https://github.com/weather-gov/api/discussions/724)


# Remote Sensing Datasets
- [Spacenet datasets](https://spacenet.ai/datasets/)
	- [video](https://www.youtube.com/watch?v=2DUcX6VGQ30)
	- 