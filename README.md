# -College_Work-DAA-
STOPWATCH:
<!DOCTYPE html>
<!-- Design by foolishdeveloper.com -->
<html lang="en">
<head>
    <title>javascript simple stopwatch</title>
    <!--Google Font-->
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@600&family=Roboto+Mono:wght@700&display=swap" rel="stylesheet">
    <!--Stylesheet-->
    <style media="screen">
      *,
*:before,
*:after{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
body{
  background: #448aff;
}
.container{
    background-color: #ffffff;
    width: 40%;
    min-width: 500px;
    position: absolute;
    transform: translate(-50%,-50%);
    top: 50%;
    left: 50%;
    padding: 20px 0;
    padding-bottom: 50px;
    border-radius: 10px;
}
.timerDisplay{
    position: relative;
    width: 92%;
    background: #ffffff;
    left: 4%;
    padding: 40px 0;
    font-family: 'Roboto mono',monospace;
    color: #0381bb;
    font-size: 40px;
    display: flex;
    align-items: center;
    justify-content: space-around;
    border-radius: 5px;
    box-shadow: 0 0 20px rgba(0,139,253,0.25);
}
.buttons{
    width: 90%;
    margin: 60px auto 0 auto;
    display: flex;
    justify-content: space-around;
}
.buttons button{
    width: 120px;
    height: 45px;
    background-color: #205e94;
    color: #ffffff;
    border: none;
    font-family: 'Poppins',sans-serif;
    font-size: 18px;
    border-radius: 5px;
    cursor: pointer;
    outline: none;
}
.buttons button:nth-last-child(2){
  background-color: #d23332;
}
.buttons button:nth-last-child(1){
  background-color: #20b380;
}
    </style>
</head>
<body>
    <div class="container">
        <div class="timerDisplay">
            00 : 00 : 00 : 000
        </div>
        <div class="buttons">
            <button id="pauseTimer">Pause</button>
            <button id="startTimer">Start</button>
            <button id="resetTimer">Reset</button>
        </div>
    </div>
 
    <script>
let [milliseconds,seconds,minutes,hours] = [0,0,0,0];
let timerRef = document.querySelector('.timerDisplay');
let int = null;

document.getElementById('startTimer').addEventListener('click', ()=>{
    if(int!==null){
        clearInterval(int);
    }
    int = setInterval(displayTimer,10);
});

document.getElementById('pauseTimer').addEventListener('click', ()=>{
    clearInterval(int);
});

document.getElementById('resetTimer').addEventListener('click', ()=>{
    clearInterval(int);
    [milliseconds,seconds,minutes,hours] = [0,0,0,0];
    timerRef.innerHTML = '00 : 00 : 00 : 000 ';
});

function displayTimer(){
    milliseconds+=10;
    if(milliseconds == 1000){
        milliseconds = 0;
        seconds++;
        if(seconds == 60){
            seconds = 0;
            minutes++;
            if(minutes == 60){
                minutes = 0;
                hours++;
            }
        }
    }
    let h = hours < 10 ? "0" + hours : hours;
    let m = minutes < 10 ? "0" + minutes : minutes;
    let s = seconds < 10 ? "0" + seconds : seconds;
    let ms = milliseconds < 10 ? "00" + milliseconds : milliseconds < 100 ? "0" + milliseconds : milliseconds;

    timerRef.innerHTML = ` ${h} : ${m} : ${s} : ${ms}`;
}


    </script>
</body>
</html>














