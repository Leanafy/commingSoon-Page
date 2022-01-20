<template>
  <div class="home">
    <header class="header">
        <div class="heade_div"> 
          <img type src="../assets/logo.png" alt="logo">
          <h1 class="line1">LEANAFY</h1>
          <h3 class="">Let's Create the Lean Way!</h3>
        </div>
     </header>
     <video class="videobg" src="../assets/leanafy.mp4" autoplay muted loop></video>
     <div class="overlay"></div>
     
    <div class="content">  
     <h2 class="cont-1">COMING SOON</h2>
     <section>
       <div class="hello">
         <div class="days">{{displayDays}} :
         <label for="days">days</label>
         </div>
         <div class="days">{{displayHours}} :
          <label for="days">hours</label>
          </div>
         <div class="days">{{displayMinutes}} :
            <label for="days">minutes</label>
          </div>    
         <div class="days">{{displaySeconds}} 
          <label for="days">seconds</label>
          </div>
      </div>
    </section>


    </div>
    
   
  </div>
</template>

<script>
export default {
  data: () => ({
    displayDays: 0,
    displayHours: 0,
    displayMinutes: 0,
    displaySeconds: 0
  }),
  computed: {
    _seconds: () => 1000,
    _minutes(){
      return this._seconds * 60;
    },
    _hours(){
      return this._minutes * 60;
    },
    _days(){
      return this._hours * 24;
    }
  },
  mounted() {
    this.showRemaining()
  },
  methods: {
    showRemaining(){
      const timer = setInterval(() =>{
        const now = new Date();
        const end = new Date(2022,0,22,10,10,10,10);
        const distance = end.getTime() - now.getTime();

        if (distance < 0){
          clearInterval(timer);
          return
        }

        const days = Math.floor((distance/this._days));
        const hours = Math.floor((distance% this._days) / this._hours);
        const minutes = Math.floor((distance % this._days) / this._minutes);
        const seconds = Math.floor((distance % this._days) / this._seconds);
        this.displayMinutes = minutes < 10 ? '0' + minutes : minutes;
        this.displaySeconds = seconds < 10 ? '0' + seconds : seconds;
        this.displayHours = hours < 10 ? '0' + hours : hours;
        this.displayDays = days < 10 ? '0' + days :days;
      }, 1000);
    }
  }

}
</script>

<style scoped>
.home{
  display: grid;
  grid-row-start: 1;
  grid-row-end: 1.5;
  /* background-image: linear-gradient(rgba(0, 0, 0, 0.5),rgba(6, 53, 46, 0.5)), url('../assets/warehouse.jpg'); */
  height: 100vh;
  max-width: 100vw;
  
}
.header{
  color: white;
  font-weight: bold;
  font-size: 30px;
  align-content: center;
  line-height: 30px;
  /* height: 20vh; */
} 
.content{
  /* font-family: 'Mochiy Pop P One', sans-serif; */
  color: rgb(220, 223, 228);
  font-weight: bold;
  font-size: 30px;
}
img{
  max-height: 70px;
  max-width: 70px;
  /* background-color: white; */
  display: inline-block;
  margin-top: 50px;
  background-color: black;
  
}
.home video{
  position: absolute;
  top: 0;
  left: 0;
  /* right: 0; */
  /* bottom: 0; */
  object-fit: cover;
  z-index: -1;
  width: 100%;
  height: 100%;
  background:linear-gradient(rgba(0, 0, 0, 0.5),rgba(6, 53, 46, 0.5)) ;  
  /* max-width: 100vw;
  max-height: 100vh; */
  /* width: 100vw; */
}

.overlay
{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(53, 52, 52, 0.5);
  mix-blend-mode: overlay;
}
.heade_div{
  color: azure;
  font-size: 18px;
  font-family: 'Nunito', sans-serif;
  letter-spacing: 4px;
  margin-top: 10px;
  
} 
.line1{
  margin-top: 10px;
}

.days{
  display: flex;
  flex-direction: column;
  align-items: center;
  font-size: 25px;
  font-variant-numeric: oldstyle-nums;
  /* letter-spacing: 4px; */
}
.hello{
  display: flex;
  -ms-flex-item-align: center;
  justify-content: center;
  /* margin-right: auto; */
  padding: 40px;
}
label{
  font-size: 12px;
  /* letter-spacing: 0; */
}
.cont-1{ 
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  letter-spacing: 40px;
  font-weight: bold;
  font-size: 30px;
  color: azure;
}


</style>
