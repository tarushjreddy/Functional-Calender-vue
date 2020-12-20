<template>
<div>
<div class="header">Calender Pro</div>
<div class="para">
<section class="calender">
  <p class="days" >Current Date:</p>
  <p class="days" >{{date}}th</p>
  <p class="days" >{{month}}</p>
  <p class="days" >{{year}}</p>
</section>

<section class="calender">
  <p class="days" >Current Time:</p>
  <p class="days" >{{hour}}:{{minutes}}:{{seconds}}</p>
 
</section>
<section class="calender">
  <p class="days" >Calender Month:</p>
  <p class="days" >{{CurrentMonth}} {{yearone}}</p>
 
</section>
<section class="calender">
  <p class="days" v-for="day in days" :key="day">{{day}} </p>
</section>
<section class="calender_dates">
   <p class="days_dates_pro" v-for="num in StartDate() " :key="num">x</p>
   <p class="days_dates" v-for="num in DateTime() " :key="num">{{num}}</p>
</section>
<section class="calender">
  <button @click="prev()" >&lt;</button>
  <button @click="next()">></button>
  <!-- <p class="days" >Current Days:</p> -->
  <!-- <p class="days" >{{StartDate()}} Days</p> -->
  
</section>
</div>

</div>
</template>

<script>


export default {
  
data(){
  return {
    month: new Date().toLocaleString('default', {month  : 'long'}),
    
    monthh: new Date().getMonth(),
    // month: new Date(),
    yearone: new Date().getFullYear(),
  
    year: new Date().getFullYear(),
    minutes: '',
    seconds: '',
    hour: '',
    date: new Date().getDate(),
    days: ['Sun', 'Mon', 'Tue', 'Wed', 'Thr', 'Fri', 'Sat']
  };
},
computed:{
  CurrentMonth(){
    console.log( new Date(10, 2020).toLocaleString('default', {month  : 'long'}))
    return new Date(this.year, this.monthh).toLocaleString('default', {month  : 'long'});
    
    
  }
},
methods:{
  
  DateTime(){

 
    return new Date(this.year, this.monthh+1, 0).getDate();
  },
MonthsTime(){
  
  setInterval(() => {
   console.log(new Date().getMinutes());
   this.minutes = new Date().getMinutes();
  
  }, 1000);

},
HoursTime(){
  
  setInterval(() => {
   console.log(new Date().getHours());
   this.hour = new Date().getHours();
  
  }, 1000);

},
StartDate(){
 
    // const year = new Date().getFullYear();

  return new Date(2020, this.monthh, 1 ).getDay();
},
next(){
  if (this.monthh == 11 || this.monthh == 0) {
    this.monthh++;
    this.yearone++;
     
  } else {
    this.month++;
     this.monthh++;


  
    
  }


},
prev(){

 if (this.monthh == 1|| this.monthh == 0 ) {
    this.monthh--;
    this.yearone--;
    
  } else {
 
  this.monthh--;


  
    
  }


},
SecondsTime(){
  
  setInterval(() => {
   console.log(new Date().getSeconds());
   this.seconds = new Date().getSeconds();
  
  }, 1000);

},},


 mounted () {
  this.SecondsTime(),
  this.MonthsTime(),
  this.HoursTime()
}

}

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@600&display=swap');
.calender{
  display: flex;

  align-items: center;
  /* justify-content: center; */
    font-family: 'Poppins', sans-serif;

}
.days{
  margin-left: 20px;
}
.days_dates{
  margin-left: 39px;
  max-width: 10px;
  text-align: center;
}
.days_dates_pro{
    margin-left: 39px;
  max-width: 10px;
  text-align: center;
  color: white;
}
.header{
  width: 100vw;
  height: 50px;
  background-color: #74b9ff;
  box-shadow: 0.5px 0.5px 10px gray;
  font-family: 'Poppins', sans-serif;
  color: white;
  font-size: 25px;
  display: flex;
  align-items: center;
  text-align: center;
  justify-content: center;
}
.calender_dates{
   display: flex;
flex-wrap: wrap;
  align-items: center;
  /* justify-content: center; */
    font-family: 'Poppins', sans-serif;
    max-width: 350px !important;
    text-align: center;
}
button{
  height: 50px;
  width: 50px;
  border: none;
  outline: none;
border-radius: 40px;
    font-family: 'Poppins', sans-serif;
margin-left: 20px;
}
button:hover{
 transition : all 200ms ease-in-out;
 background-color: #74b9ff;
     font-family: 'Poppins', sans-serif;
color: white;

}
.para{
  display: flex;
  align-items: center;
  flex-direction: column;
}
</style>
