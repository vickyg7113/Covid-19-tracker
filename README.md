<html>
 <head> 
 <meta name="viewport" content="width=device-width, initial-scale=1.0"/> 
<style>
  body{
  background-color:#DFD7F3;
}
h1{
  border:2px solid black;
  width:200px;
  margin-left:20px;
}
h2{
  margin-left:20px;
}
header{
  text-align:center;
  font-size:200%;
  font-family: Times New Roman;
  border-bottom:2px solid black;
}
.img1{
 height:30px;
 width:40px;
}
.card{
  display:flex;
  flex-wrap:wrap;
  border-bottom:2px solid black;
}
.details{
  display:flex;
  flex-wrap:wrap;
}
.totalC{
  font-size:150%;
  box-shadow:2px 2px 0px 2px grey;
  background-color:white;
  border-radius:5px;
  line-height:50px;
  margin:20px;
}

 </style>
</head> 
 <body> 
  <header> 
  Covid-19 Tracker 
  </header> 
 <script>
   fetch('https://covid-19india-api.herokuapp.com/all').then((response)=>
    {
      return response.json();
    }) 
    .then((data)=>
      {
      // console.log(data);
   
   var body =document.body;
   var h1=document.createElement("h1");
   h1.textContent="In India";
   body.append(h1);
   var card=document.createElement("div");
   card.classList.add("card");
   body.append(card);
   
   var time=document.createElement("h2");
   time.textContent="Last updated: "+data[0].last_updated;
   card.append(time);
   
   var details=document.createElement("div");
   details.classList.add("details");
   card.append(details);
   
   var totalC=document.createElement("p");
   totalC.textContent="Total Confirmed: "+data[0].confirmed_cases;
   totalC.classList.add("totalC");
   details.append(totalC);
   var totalD=document.createElement("p");
   totalD.textContent="Total Deaths: "+data[0].last_total_death_cases;
   totalD.classList.add("totalC");
   details.append(totalD);
   var totalR=document.createElement("p");
   totalR.textContent="Total Recovered: "+data[0].last_total_recovered_cases;
   totalR.classList.add("totalC");
   details.append(totalR);
   var tC=document.createElement("p");
   tC.textContent="Total Active Cases: "+data[0].last_total_active_cases;
   tC.classList.add("totalC");
   details.append(tC);
   var aR=document.createElement("p");
   aR.textContent="Active Rate: "+data[0].active_rate;
   aR.classList.add("totalC");
   details.append(aR);
   var dR=document.createElement("p");
   dR.textContent="Death Rate: "+data[0].death_rate;
   dR.classList.add("totalC");
   details.append(dR);  
  });
 </script>
 </body>
</html>
