<!DOCTYPE html>
<html>
<head>
  <title>Page Title</title>
  <meta charset="UTF-8"/>
  <link rel = "stylesheet" href="css/styles.css">
  <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
</head>
<body>
  
    <div class = "container">
        <div class="flex-container-scores">
            
            <div class="flex-item-left" id = "userScore">your score:0</div>
            <div class="flex-item-right" id = "pcScore">pc score:0</div>
          </div>

          <div class = "flex-container-result">

            <div id="user-side-pic"> 
                <img src="/images/quastion_mark.jpeg" alt="user choice" id = "userWeapon" width="250" height="250"> 
            </div>
            <div id="round-result" >
               
            </div>
            <div id="pc-side-pic">
                <img src="/images/quastion_mark.jpeg" alt="pc choice" id = "pcWeapon" width="250" height="250">
            </div>

          </div>

          <p>
              choose your weapon
          </p>

          <div class = "buttons">
            <button type="button" id = "paper" onclick="choice(this.id)">paper</button> 
            <button type="button" id = "rock" onclick="choice(this.id)">rock</button> 
            <button type="button" id = "scissors" onclick="choice(this.id)">scissors</button> 
          </div>


    </div> 





   





  <script>

      function getRandomInt(max) {
        return Math.floor(Math.random() * Math.floor(max));
    }

      function computerPlay(){
        let RndomNum = getRandomInt(3);
        switch(RndomNum){
            case 0:
                return`rock`;
            break;
            case 1:
                return`paper`;
            break;
            case 2:
                return`scissors`;
            break;
        }
    }

    function RPSRound(UserSelection , PCSelection){

       if(UserSelection == "rock"){
        switch(PCSelection){
            case "rock":
                return 0;
            break;
            case "paper":
                return 2;
            break;
            case "scissors":
                return 1;
            break;
        }
       }

       if(UserSelection == "paper"){
        switch(PCSelection){
            case "rock":
                return 1;
            break;
            case "paper":
                return 0;
            break;
            case "scissors":
                return 2;
            break;
        } 
       }

       if(UserSelection == "scissors"){
        switch(PCSelection){
            case "rock":
                return 2;
            break;
            case "paper":
                return 1;
            break;
            case "scissors":
                return 0;
            break;
        }
       }

       
        
        
    }  
    
    
    let userP ,pcP ,userScore = 0 ,pcScore = 0 , i;
    const userWeapon = document.querySelector("user-side-pic");
    const pcWeapon = document.querySelector("pc-side-pic");

    
    function choice(userP){

        pcP = computerPlay();
        if(RPSRound(userP,pcP) == 1){
            userScore++;
            document.getElementById("userWeapon").src = `images/${userP}.jpeg`;
            document.getElementById("pcWeapon").src = `images/${pcP}.jpeg`;

            document.getElementById("round-result").textContent = `${userP} wins against ${pcP}`;
            document.getElementById("userScore").textContent = `your score:${userScore}`;
        }else if(RPSRound(userP,pcP) == 2){
            pcScore++;
            document.getElementById("userWeapon").src = `images/${userP}.jpeg`;
            document.getElementById("pcWeapon").src = `images/${pcP}.jpeg`;

            document.getElementById("round-result").textContent = `${userP} loses to ${pcP}`;
            document.getElementById("pcScore").textContent = `pc score:${pcScore}`;
        }else{
        document.getElementById("userWeapon").src = `images/${userP}.jpeg`;
        document.getElementById("pcWeapon").src = `images/${pcP}.jpeg`;   
        document.getElementById("round-result").textContent = `ITS A TIE`;
        }

        if(userScore == 5){
            alert("you won!");
            location.reload(); 
            document.getElementById("round-result").textContent = ``;
        }else if (pcScore == 5){
            alert("you lost :(");
            location.reload(); 
            document.getElementById("round-result").textContent = ``;
        }
    }


    
    /*
    for(i = 0 ; i < 5; i++){
        userP = prompt("choose your play: rock , paper , scissors");
        userP = userP.toLocaleLowerCase();

        //check for valid input
        if(userP != "rock" && userP != "paper" && userP != "scissors" ){
        alert("wrong input exiting game")
            break;
        }

        pcP = computerPlay();

        //score saving
        if(RPSRound(userP,pcP) == 1){
            score++;
            alert("you won score: " + score + " pc choice " + pcP);
        }else if(RPSRound(userP,pcP) == 2){
            score--;
            alert("you lost pc choice: " + pcP + " score is: " + score);
        }else
        alert("its a tie " + score + " pc choice " + pcP);



    }
    

    if(score > 0){
        console.log("you win your score" + score);
    }else if(score < 0)
    console.log("you lose your score" + score);
    else
    console.log("its a tie");
    */
    

   

  </script>

</body>
</html>