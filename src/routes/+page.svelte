
<script>
    const options = {
        method: 'GET',
        headers: {
            'X-RapidAPI-Key': 'b42e43fb76msh6a2307be7fe7d5bp1c61dejsn5ba122f3bf6d',
            'X-RapidAPI-Host': 'weatherapi-com.p.rapidapi.com'
        }
    };

    const weatherPromise = fetch ('https://weatherapi-com.p.rapidapi.com/current.json?q=53.1%2C-0.13', options)
    
    .then((response) => response.json())
    .then((response) => {
        console.log(response)
        const { location, current} = response;
        const { country, localtime, name} = location;
        const { condition, humidity, feelslike_c, is_day, temp_c, wind_kph, wind_dir} = current;
        const { code, text} = condition;

        return {
            conditionCode: code,
            conditionText: text,
            country,
            localtime,
            name,
            humidity,
            isDay: is_day,
            feelsLike: feelslike_c,
            temperature: temp_c,
            windSpeed: wind_kph,
            windDir: wind_dir
        }
    })

    
</script>

{#await weatherPromise then weather}
        <h1>{weather.conditionText}</h1>
{/await}

<h1>Renderizado</h1>

<style>
    h1{
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    }
</style>