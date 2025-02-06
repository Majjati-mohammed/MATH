<html>
    <head>
        <link rel="icon" type="image/x-icon" href="/images/favicon.ico">
        <style>
            input{
                width: 250px;
                height: 30px;
            }
            #tracer{
                background-color: black;
                color: white;
                margin-top: 10px;
                border-radius: 10px;
                border: 1px solid black;
                margin-left: 350px;
                margin-top: -30px;
            }
            #txt{
                border-top: none;
                border-left: none;
                border-right: none;
                border-bottom: 1px solid black;
            }
            #opt{
                border: none;
                border-bottom: 1px solid black;
                margin-left: 20px;
                height: 30px;
            }
        </style>
    </head>
    <body>
        <label>Type de fonction : </label>
        <select id="opt" name="opt">
            <option value="lineaire">Lineaire</option>
            <option value="trigonometrique">Trigonometrique,Logarithmique ou autre</option>
          </select><br><br>

       
       <label>la fonction : </label>
        <input type=text value="" placeholder="Entrer une fonction" id="txt" ><br>
        <input type=button id="tracer"  onclick=func() value="Tracer"><br><br>
        <canvas id="myCanvas" width="500" height="500" style="border:1px solid grey"></canvas>
        
        
        <script>
            function func(){
            const canvas = document.getElementById("myCanvas");
            const ctx = canvas.getContext("2d");
            canvas.height = canvas.width;
            ctx.transform(1, 0, 0, -1, 0, canvas.height);
            
            let exp = document.getElementById("txt").value;
            exp = exp.toLowerCase();
            let exp1 = "Math."+exp;
            let opt = document.getElementById('opt').value;

            const xvalue = [];
            const yvalue = [];
 
            for(let x=0;x<10; x+= 0.1){
                xvalue.push(x);
                if( opt == "lineaire"){
                yvalue.push(eval(exp));
                }
                else if(opt == "trigonometrique"){
                    yvalue.push(eval(exp1));
                }
            }
            
            ctx.fillStyle = "blue";
            for(let i=0; i<xvalue.length-1; i++){
             let x = xvalue[i]*500/10;
             let y = yvalue[i]*500/10;
            ctx.beginPath();
            ctx.ellipse(x, y, 2, 2, 0, 0, Math.PI * 2);
            ctx.fill();
            }
            
        }



      /*  setInterval(function() {
    location.reload();
}, 100); */
        </script>
       
    </body>
</html>
