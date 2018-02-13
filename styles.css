var turn = true;
var active = true;
var ai = false;
var playerXSpaces = [];
var playerOSpaces = [];
var count = 0;
var aiTurnMoves = randomHit();
var cpuActive = true;


function randomHit(){
  arr = ["1","2","3","4","5","6","7","8","9"];

  for (var i = arr.length-1; i>= 0; i--){
    var index = Math.floor(Math.random() * i);
    var temp = arr[i];
    arr[i] = arr[index];
    arr[index] = temp;
  }

  return arr;
}


function takeTurn(num){
      if (turn){
        $("#" + num).html("X");
        playerXSpaces.push(num);
        check(playerXSpaces);
      }
      else{
        $("#" + num).html("O");
        playerOSpaces.push(num);
        check(playerOSpaces);
      }
      turn = !turn;
}


function aiTurn(){
  cpuActive = false;
  console.log("hi, im ai");
    //find winning moves
    var draw = searchDestroy();
    //no winning moves
    if (draw == 0){
      turn = !turn;
      // find defensive moves
      draw = searchDestroy();
      //no defensive moves
      if (draw == 0){
        draw = getAiRandom();
      }
      turn = !turn;
    }
    var flag = true;
    // loops untill valid move found, valid move executed too.
    // otherwise, a new number is drawn from the ai moves deck
    while (flag){
      if ($("#" + draw).html() == ""){
        flag = false;
        setTimeout(function(){
          takeTurn(draw);
          cpuActive = true;
        },750);
      }
      else{
        draw = getAiRandom();
      }
    }
}


function getAiRandom(){
  return aiTurnMoves.pop();
}

function searchDestroy(){
  var playerSpaces = playerOSpaces;
  var otherSpaces = playerXSpaces;
  if (turn){
    playerSpaces = playerXSpaces;
    otherSpaces = playerOSpaces;
  }

  var temp = [
  ["5","8","2"],
  ["5","4","6"],
  ["5","7","3"],
  ["5","9","1"],
  ["7","8","9"],
  ["7","4","1"],
  ["3","2","1"],
  ["3","6","9"]
];
  var count = 0;
  var hit;
  //mark player's spaces with x
  for (var h = 0; h< playerSpaces.length;h++){
    for (var i = 0; i< temp.length;i++){
      for (var j = 0; j < temp[i].length; j++){
        if (playerSpaces[h] == temp[i][j]){
          temp[i][j] = "x";
        };
      }
    }
  };

  //counts x's, if 2 then returns the hit
  for (var i = 0; i< temp.length;i++){
    for (var j = 0; j < temp[i].length; j++){
      if (temp[i][j] == "x"){
        count++;
      }
      else {
        hit = temp[i][j]
      }
    }
    if (count == 2){
      if (!otherSpaces.includes(hit)){
        return hit;
      }
    }
    hit = 0;
    count = 0;
  }
 return 0;
}






$(".space").on("mousedown", function(){
  if (($("#" + this.id).html() == "") && active && cpuActive){
    takeTurn(this.id);
    console.log("ai runs now");
    if (ai && active){
      aiTurn();
    }
  }
})


function win(tie){
  console.log("winner!");
  ai = false;
  active = false;
  if (tie){
    $(".winBanner").html("Tie");
  }
  else if (turn){
    $(".winBanner").html("X wins");
  }
  $("#top").delay(1200).toggle( "slide" );
  $("#mid").delay(1400).toggle( "slide" );
  $("#bot").delay(1600).toggle( "slide" );
  $(".winBanner").delay(1800).toggle( "slide" );
  setTimeout(function(){
    active = true;
  }, 2200);
}




function reset(){
  for (i=1;i<=9;i++){
    $("#"+ i).html("");
  }
  playerXSpaces = [];
  playerOSpaces = [];
  ai = false;
  turn = true;
  active = true;
  aiTurnMoves = randomHit();

}





function check(playerSpaces){
  console.log("checked");
   if (playerSpaces.includes('5')){
     if ( playerSpaces.includes('8') && playerSpaces.includes('2') ){
       win()
       return
     }
     else if ( playerSpaces.includes('4') && playerSpaces.includes('6') ){
       win()
       return
     }
     else if ( playerSpaces.includes('7') && playerSpaces.includes('3') ){
       win()
       return
     }
     else if ( playerSpaces.includes('9') && playerSpaces.includes('1') ){
       win()
       return
     }
   }
  if (playerSpaces.includes('7')){
     if ( playerSpaces.includes('8') && playerSpaces.includes('9') ){
       win()
       return
     }
     else if ( playerSpaces.includes('4') && playerSpaces.includes('1') ){
       win()
       return
     }
  }
  if (playerSpaces.includes('3')){
     if ( playerSpaces.includes('2') && playerSpaces.includes('1') ){
       win()
       return
     }
     else if ( playerSpaces.includes('6') && playerSpaces.includes('9') ){
       win()
       return
     }
  }
  if ((playerXSpaces.length + playerOSpaces.length == 9) && active == true){
    win(true);
  }
};

$(".winBanner").on("mousedown", function(){
  if (active){
  delay();
    $("#grid").toggle( "slide" );
    $("#players").toggle();
    $("#one").delay(500).toggle( "slide" );
    $("#playerText").delay(700).toggle( "slide" );
    $("#two").delay(900).toggle( "slide" );
    $(".winBanner").delay(900).toggle( "slide" );
    reset();
  }
});



//menu options

$("#one").on("click", function(){
  if (active){
    delay();
    ai = true;
    $("#one").delay(200).toggle( "slide" );
    $("#playerText").delay(400).toggle( "slide" );
    $("#two").delay(600).toggle( "slide" );
    playerChosen()
  }
});

$("#two").on("click", function(){
  if (active){
    delay();
    ai = false;
    $("#two").delay(200).toggle( "slide" );
    $("#playerText").delay(400).toggle( "slide" );
    $("#one").delay(600).toggle( "slide" );
    playerChosen()
  }
});

function playerChosen(){
  $(".winBanner").html("O wins");
  $(".winBanner").hide();
  $("#players").delay(800).toggle("slide",50);
  $("#symbols").delay(900).toggle("slide",50);
  $("#symX").delay(1000).toggle( "slide" );
  $("#symbolText").delay(1200).toggle( "slide" );
  $("#symO").delay(1400).toggle( "slide" );
}

$("#symO").on("click", function(){
  if (active){
    delay();
    cpuActive = false;
    if (ai){
      setTimeout(function(){
        aiTurn();
        cpuActive = true;
      }, 2500);
    };
    $("#symO").delay(200).toggle( "slide" );
    $("#symbolText").delay(400).toggle( "slide" );
    $("#symX").delay(600).toggle( "slide" );
    symbolChosen()
  }
});

$("#symX").on("click", function(){
  if (active){
    delay();
    $("#symO").delay(200).toggle( "slide" );
    $("#symbolText").delay(400).toggle( "slide" );
    $("#symX").delay(600).toggle( "slide" );
    symbolChosen()
  }
});

function symbolChosen(){
  $("#symbols").delay(850).toggle("slide");
  $("#top").show();
  $("#mid").show();
  $("#bot").show();
  $("#grid").delay(1200).toggle( "fade", 2000 );
}

function delay(){
  active = false;
  setTimeout(function(){
    active = true;
  }, 1200)
}
