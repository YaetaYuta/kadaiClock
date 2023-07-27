index.html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/snowman.css" />
    <link rel="stylesheet" href="css/style.css" />

    <title>時計</title>
</head>
<body>
    <!-- 時間とAM.PM表記
    <h1 id="time"></h1>
    <h3 id="ampm"></h3> -->

    <!-- 時計の表示 -->
<table class="boxTable">
    <tr>
        <td><div class="box1" id="makeImg"></div></td>
        <td><div class="box2" id="makeImg"></div></td>
        <td><div class="box3" id="makeImg"></div></td>
    </tr>
</table>
<!-- ボタンの配置 -->
<div class="switchArea"><button>目に悪くなります</button></div>


<div class="frasco">
    <div class="traiangle"></div>
    <div class="nose"></div>
    <div class="circle"></div>
</div>

    <script>
    "use strict"
        const body = document.querySelector('body')
        const time = document.querySelector('#time')
        const ampm =document.querySelector('#ampm');
        const sw = document.querySelector('.switchArea')
        const hourBox = document.querySelector('.box1');
        const minBox = document.querySelector('.box2');
        const secBox = document.querySelector('.box3');
        const col1 = document.querySelectorAll('value');
        let flg = 0;

    const addZero = (num) => {
        num = num < 10 ? `0${num}` : num;
        return num;
    };

    const clock=()=>{
    const now = new Date();
    let hour = now.getHours();
    let min = now.getMinutes();
    let sec = now.getSeconds();
    let millSec = now.getMilliseconds();

    // 時間の表示
    // time.innerHTML = `${addZero(hour%12)}:${addZero(min)}:${addZero(sec)}`;
    // ampm.innerHTML = hour < 12 ? `AM`:`PM`; 
    hourBox.style.transform=`rotate(${(hour+min/60)*30}deg)`;
    minBox.style.transform=`rotate(${(min+sec/60)*6}deg)`;
    secBox.style.transform=`rotate(${(sec+millSec/1000)*6}deg)`;

    requestAnimationFrame(clock);
    };
    clock();

    // ボタンを押す度に背景色が変わる
    sw.addEventListener('click', () => {
        if(flg == 0){
            body.classList.add('party');
            flg = 1;
        }
        else{
            body.classList.remove('party');
            flg = 0;
        }
    });

    
</script>
</body>
</html>
