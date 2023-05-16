# weather
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equi="X-UA-Compatible" content="IE=edge">
    <meta name="viewport"  content="width=device-width,initial-scale=1.0">

    <title> WEATHER APP </title>
    
</head>
<body>

                <div class="bg">
    
    <div class="header">
        <h1 style="color:rgb(214,147,45); text-decoration:underline;">WEATHER APP</h1>
        <div>
            <input type="text" name="box" placeholder="Enter the name..." style="font-size:18px;color:green; padding:5px 10px; outline:none; border:4; border-radius:15px; background:aliceblue;"  id="city-input">
            <br/>
            <input type="button" id="search-btn" value="Search" style=" color:rgb(18, 233, 18);" >                                  
        </div>
    </div>
        <div class="Weather">
            <h2 id="city" style="font-size: 30px; text-align: center; padding-left: 130px; color:black;">_________</h2>
            
            <div class="temp-box">
                <img src="https://tse2.mm.bing.net/th?id=OIP.XwQR3nYxLJ5Xt_SkDl6cogHaHa&pid=Api&P=0" id="img" style="width: 20%; height: 20%; border-radius: 0%; background: rgba(240,248,255,0.4);">
                
                <p id="temperature" style="font-size: 50px; margin: 4px; margin-left: 30px; margin-bottom: 10px; color:blue;">26°C</p>
            </div>
            <span id="clouds" style="color:green;font-size:35px;">Broken clouds</span>
        </div>
        <div class="divider1" style="height: 1px; background-color: red; margin: 2rem 0;"></div>
        <div class="forecastH">
            <p class="cast-header" style="color:rgb(55, 255, 0); font-size:32px"><i>LIVE DATA:</i></p>
            <div class="templist">
                <div class="next">
                    <div>
                        <p class="time" style="color:white;font-size:26px"><span id="wind speed">MIN/MAX TEMPERATURE:</span></p>
                        <p style="color:aqua;font-size:22px;"> <span id="min">29 °C</span>  / <sapn id="max">25 °C</sapn> </p>
                    </div>
                    
                </div>
                <div class="next">
                    <div>
                        <p class="time" style="color:white;font-size:26px;">HUMIDITY:</p>
                        <p style="color:aqua;font-size:22px;"><span id="humid">60g/kg</span></p>
                    </div>
                    <p class="dc" style="color:white;font-size:26px;">WIND SPEED:</p>
                    <p class="desc" style="color:aqua;font-size:22px;"><span id="wind">2 km/hr</span></p>
                </div>
            

    <style>

     .html{
        height:100%;

    }

.header{

    padding:1rem 5rem;
    font-family:"Papyrus", "Copperplate", fantasy;
    background:linear-gradient(45deg,rgba(183,204,246,0.7),rgba(7,43,127,067));
    

    
}
.bg{
background-image:url('https://images.pexels.com/photos/1025349/pexels-photo-1025349.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2');

background-repeat:no-repeat;
width:100vw;
height:180vh;
background-position:center;


}

    
      
.header h1{
    color:rgb(214,147,45);
    text-decoration:underline;
    padding-left:500px;
}
#input{
    font-size:18px;
    padding:5px 10px;
    outline:none;
    border:4;
    border-radius:15px;
    background:aliceblue;
    }
#search{

    background:cadetblue;
    padding:2px 20px;
    color:alice blue;
    outline:4;
    font-size:17px;
    border-radius:15;
    cursor:pointer;


    }
     

    .main{
   
   
    color:light green;


    padding: 3rem 5rem;
    }
    .Weather{
        text-align: center;
        color: blue;
    }
    
    .Weather img{
        width: 40%;
        height: 40%;
        border-radius: 0%;
        background: rgba(240,248,255,0.4);
    }
    
    #city{
        font-size: 30px;
        text-align: center;
        padding-left: 130px;
    }
    
    #temperature{
        font-size: 50px;
        margin: 4px;
        margin-left: 30px;
        margin-bottom: 10px;
    }
    
    .temp-box{
        justify-content: center;
        padding-left: 180px;
    }
    
    .divider1, .divider2{
        height: 1px;
        background-color: aliceblue;
        margin: 2rem 0;
    }



    .divider2{
            height:5px;
            width:30px;
            margin:0 auto;

        }
    
    .forecstD{
        margin:20px 50px;
        color: beige;


        }
        
        .weekF{
            display:grid;
            grid-template-columns:repeat(4,1fr);
            
        }
        .h2{
            font-size:10px;
            text-align:center;
            padding-left:80px;
        }

        </style>
    
</div>

<script>
   
   document.getElementById("search-btn").addEventListener("click", () =>{
  let city = document.getElementById("city-input").value;

     let API_KEY = "1d803e5396da34500034036a8116b173";
    const URL = 'https://api.openweathermap.org/data/2.5/weather';
    console.log(city)
        const Full_Url = `${URL}?q=${city}&appid=${API_KEY}&units=metric`;

    async function checkWheather(){
      let res = await fetch(Full_Url);
      let data = await res.json();
      console.log(data)
         
      
     //input u

    document.getElementById("temperature").innerHTML = data.main.temp + "°C";
    document.getElementById("max").innerHTML = data.main.temp_max + "°C";
    document.getElementById("min").innerHTML = data.main.temp_min + "°C";
    document.getElementById("city").innerHTML = data.name;
    document.getElementById("humid").innerHTML= data.main.humidity + "g/kg";
    document.getElementById("wind").innerHTML = data.wind.speed + "Km/hr"
    document.getElementById("clouds").innerHTML = data.weather[0].description;
    document.getElementById("clouds").innerHTML = data.weather[0].description;
    document.getElementById("clouds").innerHTML = data.weather[0].description;
    document.getElementById("clouds").innerHTML = data.weather[0].description;
    
    if(data.weather[0].description == "mist"){
        document.getElementById("img").src = "mist.png"
    }
    else if(data.weather[0].description =="overcast clouds"){
        document.getElementById("img").src = "clouds.png"
    }
    else if(data.weather[0].description =="clear sky"){
        document.getElementById("img").src = "clear.png"
    }
    else if(data.weather[0].description =="rainy"){
        document.getElementById("img").src = "rain.png"
    }


    }
    
   
    checkWheather()
   });  

    



    </script>
    </body>
    </html>
    
